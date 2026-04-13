##  Air Foil design based on Bezier curves - graph. editor
![pikFoil](/assets/images/pikFoil80.png)
<br>Editor uses Bezier curves of 3 and 4 degree. The vector form looks like:
![Bezier3,4](/assets/images/03.png)
<br>A vector is a point with two coordinates: x, y .<br>
Control point __P4 (green) of B4__ — controls the middle part of the curve.

The editor has seven ways to generate airfoils :

* __B2__ &nbsp; - two Bezier-3
* __B2+__ - two Bezier-4
* __B3+__ - two Bezier-4 & B3
* __B4__ &nbsp; - four Bezier-3
* __B5__ &nbsp; - five Bezier-3
* __HB+__ - __Half__ of foil: two B4 &nbsp; & &nbsp; __B3__ - camber - midle line
* __HA__ &nbsp; - __Half__ of foil: two B3 &nbsp; & &nbsp; __Arc__ camber - midle line

