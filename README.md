##  Air Foil design based on Bezier curves - graph. editor
![pikFoil](/assets/images/pikFoil80.png)
<br>__The editor uses Bezier curves of 3 and 4 degree__. The vector form looks like:
![Bezier3,4](/assets/images/03.png)
<br>A vector is a point that has two or more coordinates.<br>
Control point __P4 (green) of B4__ — controls the middle part of the curve.

The editor has seven ways to construct airfoils :

* __B2__ &nbsp; - two Bezier-3
* __B2+__ - two Bezier-4
* __B3+__ - two Bezier-4 &nbsp;& &nbsp;Bezier-3
* __B4__ &nbsp; - four Bezier-3
* __B5__ &nbsp; - five&nbsp; Bezier-3
* __HB__ &nbsp; - __Half__ of foil : &nbsp;two Bezier-4 &nbsp; & &nbsp; Bezier-3 &nbsp;camber
* __HA__ &nbsp; - __Half__ of foil : &nbsp;two Bezier-3 &nbsp; & &nbsp; __Arc__ &nbsp;camber line

After selecting the airfoil construction method, you can drag the control points to achieve the desired shape.

Editor supports __"Foil Buffer"__ to store intermediate steps or foil series.
How to control editor and use window graphics is described in __&lt;Help-F1>__.

Result saves in text file with __.foil__ extension. It contains all Bezier curves( Control Points: P1...P5 )
with comments how to use them. In addition it contains array of the __"discrete" airfoil points( x,y )__.
Points are selected in accordance with a curvature to ensure a deviation less than 0.0002 .

It is convenient to evaluate airfoil characteristics with <a href='http://www.mh-aerotools.de/airfoils/javafoil.htm'>"JavaFoil of Martin Hepperle"</a>.

To copy airfoil discrete points to the system ClipBoard, press the button __"ClipBoard"__.<br>
Go to the &nbsp;__"JavaFoil"__ ( it must be run __in parallel with pikFoil__ ).<br>
In the tab: __"Geometry"__ press the button __"Paste( Text )"__.<br>
In the tab: __"Polar"__ &nbsp; &nbsp; &nbsp; &nbsp; press the button __"Analyze it"__.<br>

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __Curvature issue__

In general case two Bezier curves are joined with a continuous first derivative, but have a gap 
in the __curvature( k__ ) - the reciprocal of the __curvature radius R__ . To see curvature gaps, press the button __"Curvature"__ and use __ZOOM__. 

![curvature](/assets/images/k.png)

__pikFoil__ has additional service to ensure continuous curvature -__"Smooth"__.
Use checkbox "Smooth" ON/OFF this service. When the service is activated, __pikFoil__ finds the gap and try to remove it by adding special functions,
which slightly change __the Bezier curves :__<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;__Bs(t)__ = __B(t)__+ f0(t)\*__K0__+ f1(t)\*__K1__ ,<br>
where: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; __K0, K1__ - vectors of __smooth coefficients__ (extends the Bezier Control Points),<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f0, f1 &nbsp;- scalar functions :<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f0(t) = __.5 * t^2 * (1-t)^3__, &nbsp; f0(0)=f0(1) = f0'(0)=f0'(1) = __0__, &nbsp; f0"(0)=__1__, &nbsp;f0"(1)=__0__ ;<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f1(t) = __.5 * t^3 * (1-t)^2__, &nbsp; f1(0)=f1(1) = f1'(0)=f1'(1) = __0__, &nbsp; f1"(0)=__0__, &nbsp;f1"(1)=__1__ .<br> 

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __install & run__

Program compiled with __JAVA-21__ (can be run under later JAVA versions) and packed into the __pikFoil.jar__ file.<br>
It is enough __jre package__ to run pikFoil. &nbsp;__JRE__ is free to download(~60 MB): <a href='https://www.azul.com/downloads/?os=windows&architecture=x86-64-bit&package=jre#zulu'>Azul Downloads</a><br>

Standard run: &nbsp;> __java &nbsp; -jar &nbsp; pikFoil.jar__ &nbsp; [ saved_Foil ]<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;or &nbsp; > __pikFoil[.bat]__ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[ saved_Foil ]<br>
__shortcut__ &nbsp;for &nbsp; &nbsp; &nbsp; __pikFoil. bat__ &nbsp; &nbsp; &nbsp; can be placed on the __desktop__ ( use __pikFoil.ico__ ) &nbsp; __# recommended__<br>

__pikFoil__ works fine under __Linux__ (tested in Mint 21).

Examples:<br>
![half_B5](/assets/images/half_B5.png)
![curvgap](/assets/images/curvgap.png)
![smooth](/assets/images/smooth.png)
