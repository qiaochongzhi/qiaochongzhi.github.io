---
layout: post
title: Windows下安装fftw的方法
tags: Date-Struct
---

最近由于某些原因需要在Windows下面使用fftw，参照网上的教程并没有安装成功。最后经过一番努力后终于安装成功，下面是我的安装过程：

### 获取fftw
首先由[官网](http://www.fftw.org/install/windows.html)获取fftw最新版，并解压。

### 生成并安装相关文件
在解压文件夹下用CMD运行[^1]如下指令[^2]：
{% highlight bash %}
lib /def:libfftw3-3.def
lib /def:libfftw3f-3.def
lib /def:libfftw3l-3.def
{% endhighlight %}
但是在我的电脑上这一步由于设置路径的原因并没有成功，于是我使用了简单粗暴的方法，即将`libfftw3-3.def`，`libfftw3f-3.def`以及`libfftw3l-3.def`全部复制到VS下的bin文件夹中。下面是我电脑上的路径：
{% highlight bash %}
C:/Program Files (x86)/Microsoft Visual Studio 12.0/VC/bin
{% endhighlight %}
之后再在该路径下运行上述指令将生成的三个`.lib`文件，将这三个放到如下目录：
{% highlight bash %}
C:/Program Files (x86)/Microsoft Visual Studio 12.0/VC/lib
{% endhighlight %}
之后可以选择清理下`bin`中的文件。将解压文件夹中的`libfftw3-3.dll`和`libfftw3f-3.dll`以及`libfftw3l-3.dll`文件复制到相应的系统文件中，这样以后执行比较方便。如果是32位系统就放到`C:/Windows/System32`中，如果是64位系统则放置在`C:/Windows/SysWOW64`中。最后将`fftw3.h`放入如下目录[^sys]即可。
{% highlight bash %}
C:/Program Files (x86)/Microsoft Visual Studio 12.0/VC/include
{% endhighlight %}
这样就初步完成了fftw的安装。

### Visual Studio中使用fftw
下面在Visual Studio中使用fftw，首先建立一个项目`test`，之后选择`项目`--`test属性`--`链接器`--`输入`--`附加依赖项`，在其中添加我们的3个lib文件[^4]：
{% highlight bash %}
libfftw3-3.lib
libfftw3f-3.lib
libfftw3l-3.lib
{% endhighlight %}

下面是一个测试代码[^5]：
{% highlight C++ %}
#include "fftw3.h"  
#include <stdio.h>  
#define N 8  
int main()
{
  int i;
  fftw_complex *din, *out;
  fftw_plan p;
  din = (fftw_complex*)fftw_malloc(sizeof(fftw_complex) * N);
  out = (fftw_complex*)fftw_malloc(sizeof(fftw_complex) * N);
  if ((din == NULL) || (out == NULL))
  {
    printf("Error:insufficient available memory\n");
  }
  else
  {
    for (i = 0; i < N; i++)
    {
      din[i][0] = i + 1;
      din[i][1] = 0;
    }
  }
  p = fftw_plan_dft_1d(N, din, out, FFTW_FORWARD, FFTW_ESTIMATE);
  fftw_execute(p); /* repeat as needed */
  fftw_destroy_plan(p);
  fftw_cleanup();
  for (i = 0; i < N; i++)/*OUTPUT*/
  {
      printf("%f,%fi\n", din[i][0], din[i][1]);
  }
  printf("\n");
  for (i = 0; i < N; i++)/*OUTPUT*/
  {
      printf("%f,%fi\n", out[i][0], out[i][1]);
  }

  if (din != NULL) fftw_free(din);
  if (out != NULL) fftw_free(out);
  getchar();
  return 0;
}
{% endhighlight %}
结果应为：
{% highlight bash %}
1.000000,0.000000i
2.000000,0.000000i
3.000000,0.000000i
4.000000,0.000000i
5.000000,0.000000i
6.000000,0.000000i
7.000000,0.000000i
8.000000,0.000000i

36.000000,0.000000i
-4.000000,9.656854i
-4.000000,4.000000i
-4.000000,1.656854i
-4.000000,0.000000i
-4.000000,-1.656854i
-4.000000,-4.000000i
-4.000000,-9.656854i
{% endhighlight %}
在成功运行后可以去官网学习一下fftw的[文档](http://www.fftw.org/fftw3.pdf)。

### 参考资料
[^1]: [FFT的C语言库FFTW的Windows和linux安装使用方法](http://anony3721.blog.163.com/blog/static/511974201312322910595/)
[^2]: [Windows Installation Notes](http://www.fftw.org/install/windows.html)
[^4]: [Windows平台安装fftw](http://www.tuicool.com/articles/ZbuIfa)
[^5]: [Windows安装和使用fftw](http://blog.csdn.net/bendanban/article/details/23002257)
[^sys]: [Windows中System32和SysWOW64的区别](http://icbcling.blog.163.com/blog/static/107312059201281113229761/)