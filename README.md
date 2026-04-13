##  Air Foil design based on Bezier curves - graph. editor
![pikFoil](/assets/images/pikFoil80.png)
<br>Editor uses Bezier curves of 3 and 4 degree. The vector form looks like:
![Bezier3,4](/assets/images/03.png)
<br>A vector is a point with two coordinates: x, y .<br>
Control point __P4 (green) of B4__ — controls the middle part of the curve.

The editor has seven ways to construct airfoils :

* __B2__ &nbsp; - two Bezier-3
* __B2+__ - two Bezier-4
* __B3+__ - two Bezier-4 &nbsp;& &nbsp;Bezier-3
* __B4__ &nbsp; - four Bezier-3
* __B5__ &nbsp; - five Bezier-3
* __HB+__ - __Half__ of foil : &nbsp;two Bezier-4 &nbsp; & &nbsp; Bezier-3 &nbsp;camber
* __HA__ &nbsp; - __Half__ of foil : &nbsp;two Bezier-3 &nbsp; & &nbsp; __Arc__ &nbsp;camber line

After selecting the airfoil construction method, you
can drag the control points to achieve the desired airfoil shape.

Editor supports "Foil Buffer" to store intermediate steps or foil series.

How to control editor and use window graphics is described in __&lt;Help-F1>__.

Result saves in text file with __.foil__ extension. It contains all Beziers as list of "Bezier Control points": P1...P5
with comments how to use them. In addition it contains "discrete" airfoil points(x,y) array.
Discrete points are selected in accordane with curvature to ensure a deviation less than 0.0002 .

It is convenient to evaluate airFoil characteristics with <a href='http://www.mh-aerotools.de/airfoils/javafoil.htm'>"JavaFoil of Martin Hepperle"</a>.

To copy airfoil discrete points to the system ClipBoard, press the button __"ClipBoard"__.<br>
Go to the &nbsp;__"JavaFoil"__ ( it must be run __in parallel with pikFoil__ ).<br>
In the tab: __"Geometry"__ press the button __"Paste( Text )"__.<br>
In the tab: __"Polar"__ &nbsp; &nbsp; &nbsp; &nbsp; press the button __"Analyze it"__.<br>

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; __Curvature issue__

In general case two Bezier curves are joined with a continuous first derivative, but have a gap 
in the __curvature( k__ ) - the reciprocal of the __curvature radius R__ :

![curvature](/assets/images/k.png)

__pikFoil__ has additional service to ensure continuous curvature - __"Smooth"__.
