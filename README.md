##  Air Foil design based on Bezier curves - graph. editor
![pikFoil](/assets/images/pikFoil80.png)
<br>Editor uses Bezier curves of 3 and 4 degree. The vector form looks like:
![Bezier3,4](/assets/images/03.png)
<br>A vector is a point with two coordinates: x, y .<br>
Control point __P4 (green) of B4__ — controls the middle part of the curve.

The editor has seven ways to generate airfoils :

* B2 &nbsp- two Bezier-3
* B2+ - two Bezier-4
* B3+ - two Bezier-4 & B3
* B4 &nbsp;- four Bezier-3
* B5 &nbsp;- five Bezier-3
* HB+ - half of foil: two B4 & B3 - camber
* HA &nbsp;- two B3 & Height of Arc( camber )
