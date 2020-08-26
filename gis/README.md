# GIS

- A geographic information system is a conceptualized framework that provides the ability to capture and analyze spatial and geographic data.

## Coordinates System

### Geographic Coordinate System

- It is a coordinate system based on laditude, longitude.
- It is used to describe a position on a sphere or in any 3-D space.
- In GIS, decimal degrees are often used, other than degrees minutes and seconds.
  - convert unit from degrees minutes and seconds to decimal degrees `D + M/60 + S/3600`
- `EPSG` code can identify different geographic coordinate systems
  - `EPSG` Geodetic Parameter Dataset (also EPSG registry) is a public registry of spatial reference systems, Earth ellipsoids, coordinate transformations and related units of measurement.
  - Each entity is assigned an EPSG code between 1024-32767, along with a standard machine-readable well-known text (WKT) representation.
  - The EPSG code `4326` is the commonly used geographic coordinate system `WGS84`(World Geodetic System 1984)

#### Latitude

- determine how much north or south the point is, on earth.
- This is refered as the `Y` coordinate
- On equitor, the latitude is 0 degree.
- in the northern hemisphere the latitude is positive.
- in the southern hemisphere the latitude is negative.
- On the north or south pole the absolute latitude value is 90.

#### Longitude

- determine how much east or west the point is, on earth.
- This is refered as the `X` coordinate
- The prime meridian is a line on earh drawn from the north pole to south pole where all points on this line has longtitude as 0 degree.
- The current prime meridian adopts Greewich Meridian. The line passes the Royal Observatory, Greenwich, in London, England.
- Any point located on the east side of the prime meridian has a positive longitude value.
- Any point located on the west side of the prime meridian has a positive negative value.
- Longitude uses 180 degree to represent location that is complete on the oppsite side of the earth, for any given point on the prime meridian line.

### Projected Coordinate System

- It is used to project a coordinate system onto a plane and describe the coordinate with a plane(map or screen).
- Distortion always happens when project 3D coordinate to 2D.
- A project method can only preserve one property of a 3D coordinate and distort the other 3 properties.
- Types of projection:
  - Equal-area projections(preserve area)
    - Gall-Peters
  - Equidistant projections(fully preserve distant)
  - Conformal projections(fully preserve shape and angle)
    - Mercator - commonly used by web maps
  - Azimuthal projections(fully preserve direction)
  - Compromise projection(partially preserve any two or more propertes)
    - Winkel Tripel(partially preserve shape and area)
  - Local projections - focus on dispalying a local slice for a specific country, area or project.
    - Universal Transverse Mecator
    - State Plane(USA)
    - National Grid of Great Britian(UK)
    - Indian Grid System(India)
