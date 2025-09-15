# toroCVSreport
toro C-Validation-Suite reports

### Table of content
* [Preface](README.md#Preface)
* [Basic concept](README.md#basic-concept)
* [Introduction: math.h](README.md#introduction-mathh)
    * [Test results: math.h](README.md#test-results-mathh)


## Preface
**toroCVS** is a proprietary test suite to validate the **toro C Library**.

![](documents/toroCVS.png)

### Basic concept
The **toro C Library** is validated against the original **Microsoft C Library** in **Visual Studio 2022** — the **Microsoft C Library** is the reference implementation.

The **toro C Library** is a submodule of the **toroCVS** superproject. Each **toro C Library** function has a corresponding test module in **toroCVS**. Because modern PCs have high processing speed and large storage capacity, the test suite generally uses a brute-force strategy for validation.

The test suite generates the required test parameters, invokes the **DUT** (device under test — a math.h function) with these parameters, and reports the results to a .LOG file in the build folder.

The test is executed on both:
* **toro C Library**–linked test application
* **Microsoft C Runtime Library**–linked test application

# Introduction: math.h
![](documents/logfolder.png)

Each .LOG file is inspected carefully to identify bugs and miscalculations. For **math.h** functions this is a challenging task because the results of floating-point calculations may differ in the low-significance bits yet still be correct. It is difficult to identify true miscalculations in millions of trace lines with around one million non-relevant differences.

These natural differences arise because the respective libraries use different arithmetic units: the **8087 FPU** versus the **SSE unit**. For example, for the **`pow()`** function:

![](documents/powdiff2.png)

## Test results: math.h
The test results of all **math.h** functions **toro C Library** vs. **Microsoft C Library** are compared for each function in the table below:<br>
(to keep diff file size small, only 15 lines around differences are shown)<br>

<table>
<th>toro C Library </th> <th >MSFT C Library</th>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/acos.html>acos()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/asin.html>asin()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/atan.html>atan()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/atan2.html>atan2()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/ceil.html>ceil()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/cos.html>cos()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/cosh.html>cosh()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/exp.html>exp()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/fabs.html>fabs()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/floor.html>floor()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/fmod.html>fmod()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/frexp.html>frexp()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/ldexp.html>ldexp()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/log.html>log()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/log10.html>log10()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/modf.html>modf()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/pow.html>pow()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/sin.html>sin()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/sinh.html>sinh()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/sqrt.html>sqrt()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/tan.html>tan()</a></th></tr>
<tr><th colspan="2"><a href=https://cdn.githubraw.com/KilianKegel/toroCVSreport/main/report/math_h/x64/tanh.html>tanh()</a></th></tr>
</table
