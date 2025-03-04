# Extensions for common Windows app geometric transforms

I created these extension methods because I found myself using them extensively in a Windows control library I built.

[return to readme](../readme.md)

## Transform a shape defined by a Vector3 collection

```c#
public static Vector3[] ApplyTransform( this Vector3[] points, Matrix4x4 transform )
```

Applies `transform` to the `points` collection, return a transformed collection of `Vector3` points.

[return to top](#extensions-for-common-windows-app-geometric-transforms)

## Transform a Rectangle2D object

```c#
 public static Rectangle2D ApplyTransform(
     this Rectangle2D rectangle,
     Matrix4x4 transform,
     CoordinateSystem2D? coordinateSystem = null
 )
 ```

 Applies `transform` to `rectangle`, returning a new `Rectangle2D` object. You can change the coordinate system used to create the new `Rectangle2D` object by specifying an optional `coordinateSystem` value.

[return to top](#extensions-for-common-windows-app-geometric-transforms)

## Transform Rectangle2D objects to and from display space

 I find the Windows graphical display environment monumentally confusing in one particular aspect: increasing the value of the **Y coordinate** moves you _down the screen_, exactly backwards from normal mathematical usage.

 To try and keep things straight, I consider the Windows coordinate system to be _display space_, and the normal/mathemtical system _real space_.

 I've often found it useful to be able to move rectangles between these two systems. The library contains two extension methods to do this.

```c#
public static Rectangle2D ToDisplaySpace( this Rectangle2D rectangle, Vector3 viewport )
```

`ToDisplaySpace()` remaps a `Rectangle2D` object from _real space_ to a _display space_ defined by a `Vector3` viewport. The elements of the vector are interpreted as the dimensions of the _display space_.

```c#
public static Rectangle2D FromDisplaySpace( this Rectangle2D rectangle, Vector3 viewport )
```

`FromDisplaySpace()` remaps a `Rectangle2D` object from _display space_ to a _real space_ defined by a `Vector3` viewport. The elements of the vector are interpreted as the dimensions of the _real space_.

[return to top](#extensions-for-common-windows-app-geometric-transforms)

## Create a perpindicular vector

```c#
public static Vector3 Perpendicular( this Vector3 vector, float magnitude = 1 )
```

`Perpendicular()` returns a `Vector3` that is perpendicular to the proviced `vector`. You can optionally resize the perpindicular by providing a `magnitude` other than 1.

A `magnitude` less than or equal to zero is defaulted to a value of 1.

[return to top](#extensions-for-common-windows-app-geometric-transforms)
