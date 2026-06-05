##  Air Foil design based on Bezier curves - graph. editor
![pikFoil](/assets/images/pikFoil80.png)
<br>__The editor uses Bezier curves of 3 and 4 degree__. The vector form looks like:
![Bezier3,4](/assets/images/03.png)
<br>A vector is a point that has two or more coordinates.<br>
Control point __P4 (green) of B4__ — controls the middle part of the curve.

The editor has six ways to construct airfoils :

* __B2+__ - two Bezier-4
* __B3+__ - two Bezier-4 &nbsp;& &nbsp;Bezier-3
* __B4__ &nbsp; - four Bezier-3
* __B5__ &nbsp; - five&nbsp; Bezier-3
* __HB__ &nbsp; - __Half__ of foil : &nbsp;two Bezier-4 &nbsp; & &nbsp; Bezier-3 &nbsp;camber
* __HA__ &nbsp; - __Half__ of foil : &nbsp;two Bezier-3 &nbsp; & &nbsp; __Arc__ &nbsp;camber line

After selecting the airfoil construction method, you can drag the control points to achieve the desired shape.

Editor supports __"Foil Buffer"__ to store intermediate steps or foil series.
How to control editor and use window graphics is described in __&lt;Help-F1>__.

Result saves in text file with __.foil__ extension. It contains all Bezier curves( Control Points: P0...P4 )
with comments how to use them. In addition it contains array of the __"discrete" airfoil points( x,y )__.
Points are selected in accordance with a curvature to ensure a deviation less than 0.0002 .

It is convenient to evaluate airfoil characteristics with <a href='http://www.mh-aerotools.de/airfoils/javafoil.htm'>"JavaFoil of Martin Hepperle"</a>.

To copy airfoil points to the system ClipBoard, press the button __"ClipBoard"__.<br>
Go to the &nbsp;__"JavaFoil"__ ( it must be run __in parallel with pikFoil__ ).<br>
In the tab: __"Geometry"__ press the button __"Paste( Text )"__.<br>
In the tab: __"Polar"__ &nbsp; &nbsp; &nbsp; &nbsp; press the button __"Analyze it"__.<br>
See the last screenshot in the examples below.

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __Click Sequence after ClipBoard__

To evaluate the profile characteristics you must click the mouse 4 times in the __JavaFoil__ application.<br>
__"ClipBoard Click Sequence"__ service allows you to automate this process.<br> 
You simply specify a __sequence of screen coordinates__ for a programmatic mouse click after __"ClipBoard"__.<br>

After selecting the menu item: __ClipBoard Click Sequence__ or by using the hotkey: '__C__', you add
desired screen locations with the mouse. Service window is a text. You can view, edit and even clear it at any time.<br> 

Example for __JavaFoil__ ( must run in parallel with __pikFoil__ ):<br>
 - On the main window of __pikFoil__ press key '__C__' or click Right mouse: __menu/ bottom point__ ;
 - pres button: __ADD__ , move mouse and click __JavaFoil__ Tab: __"Geometry"__ &nbsp; --> &nbsp; 1. 1176, 41 &nbsp; &nbsp; ! lines like these<br>
 - pres button: __ADD__ , move mouse and click button: __"Paste( Text )"__ &nbsp; &nbsp; &nbsp;&nbsp; --> &nbsp; 2. 1405, 758 &nbsp; ! will be added<br>
 - pres button: __ADD__ , move mouse and click __JavaFoil__ Tab: __"Polar"__ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; --> &nbsp; 3. 1596, 38<br>
 - pres button: __ADD__ , move mouse and click button: __"Analyze it"__ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; --> &nbsp; 4. 1348, 719<br>

The sequence of 4 clicks is ready. To close window press key: __Esc__ or standard __[x]__-window top right.

Now, each time you press the __pikFoil ClipBoard__, the specified __Click Sequence__ will be performed.<br>
There's no longer need to perform 4 clicks in __JavaFoil__. You will immediately see changes in airFoil's aerodynamics.

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __Curvature issue__

In general case two Bezier curves are joined with a continuous first derivatives, but have a gap
in the __curvature( k__ ) - the reciprocal of the __curvature radius R__ . To see curvature gaps, press the button __"Curvature"__ and use __ZOOM__.

![curvature](/assets/images/k.png)

__pikFoil__ has two services to ensure continuous curvature. Both services slightly change the Bezier curves.<br>
Unfortunately, in the current version, the __curvature is not differentiable (only continuous) at the connection points__.

__1.__ Button __"Smooth Rot."__ - attempts to eliminate curvature gaps by rotating __"yellow lines"__ with Control Points around a central Point.
In some cases this gives good results. The downside of this service is that it is irreversible.
Before starting the service, it is recommended to save the airfoil in the __Foil Buffer__ (press button __ClipBoard__).
In case of unsuccessful result, the previous state can be returned by press key: __E -"End of Buffer"__( see commands of the Foil Buffer ).

__2.__ Checkbox __"Smooth Add."__ When the service is __ON__ - activated/ selected , __pikFoil__ finds a gap and tries to remove it by adding special functions.<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; __Bs(t)__ = __B(t)__+ f0(t)\*__K0__+ f1(t)\*__K1__ ,<br>
where: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; __K0, K1__ - vectors of __smooth coefficients__ (extends the Bezier Control Points),<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f0, f1 &nbsp;- scalar functions :<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f0(t) = __.5 * t^2 * (1-t)^3__, &nbsp; f0(0)=f0(1) = f0'(0)=f0'(1) = __0__, &nbsp; f0"(0)=__1__, &nbsp;f0"(1)=__0__ ;<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; f1(t) = __.5 * t^3 * (1-t)^2__, &nbsp; f1(0)=f1(1) = f1'(0)=f1'(1) = __0__, &nbsp; f1"(0)=__0__, &nbsp;f1"(1)=__1__ .<br>

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __install & run__

Program is compiled with __JAVA-21__ (can be run under later JAVA versions) and is packed into the __pikFoil.jar__ .<br>
It is enough __JRE package of JAVA__ to run pikFoil. &nbsp;__JRE__ is free to download(~60 MB): <a href='https://www.azul.com/downloads/?os=windows&architecture=x86-64-bit&package=jre#zulu'> Azul Downloads</a><br>

Standard run: &nbsp;> __java &nbsp; -jar &nbsp; pikFoil.jar__ &nbsp; [ saved_Foil ]<br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;or &nbsp; > __pikFoil[.bat]__ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[ saved_Foil ]<br>
__shortcut__ &nbsp;for &nbsp; &nbsp; &nbsp; __pikFoil. bat__ &nbsp; &nbsp; &nbsp; can be placed on the __desktop__ ( use __pikFoil.ico__ ) &nbsp; __# recommended__<br>

__pikFoil__ works fine under __Linux__ (tested in Mint 21).

&nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; __Template viewer__

You can copy airFoil data as __array of x,y__  to the ClipBoard or to the File and load it as __Template__( in case clipboard, file name = ClipBoard ).
Data can be taken from any source: NACA or other airFoil Libraries.

Examples:<br>
![half_B5](/assets/images/half_B5.png)
![curvgap](/assets/images/curvgap.png)
![smooth](/assets/images/smooth.png)
![pikFoil_javaFoil](/assets/images/pikMH.png)

