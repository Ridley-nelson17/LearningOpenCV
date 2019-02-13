# LearningOpenCV
A reposiaitory that demonstrates how to use Java and OpenCV for Vision Processing

### Index

- [Usage/Building on Desktop](/README.md#usagebuilding-on-desktop)
- [Bugs](/README.md#bugs)
- [Sources](/README.md#sources)
- [The Docs](/README.md#the-docs)
   - [The Camera Class](/README.md#camera)
   - [The Target Class](/README.md#target)
   - [Connecting to a Raspberry Pi](/README.md#connecting-to-a-raspberry-pi)
   - [Finding Angles](/README.md#)
   - [Controling Motors](/README.md#)
   - [](/README.md#)

=================================================================================
### Usage/Building on Desktop
1. Download the .zip archive and move it over to IntelliJ.
2. Make sure there is a camera attached to the computer you are using, it doesn't matter if it is ther built in one facing you
3. Run as a java application
4. Hold up the vision target in the cameras range of view and watch the console blow up

=================================================================================

### Bugs
Currently, I know that there is one issue in `Scannable.java` that throws an IOException probably because I have not implamented the class properly

### Sources
Java 11, OpenCV

# Docs

## Camera

   ### Setting the Camera Input Port
   
   ### Sending the output to a Server

## Target
   
   ### Combining The Objects
   
   ### Setting the target
   ```
   public class Target {

    private double horizontalAngle, verticalAngle;

    private double percentArea;

    private double skew;

    private RotatedRect boundary;

    /**
     * Creates a target.
     * @param horizontalAngle The horizontal angle from the center of the camera to the center of the target in degrees.
     * @param verticalAngle The vertical angle from the center of the camera to the center of the target in degrees.
     * @param percentArea The percent area of the target to the image's area [0, 100] in percentage.
     * @param skew The skew of the target (rotation angle) in degrees [-90, 90].
     * @param boundary The bounding rotated rectangle of the target.
     */
    public Target(double horizontalAngle, double verticalAngle, double percentArea, double skew, RotatedRect boundary) {
        this.horizontalAngle = horizontalAngle;
        this.verticalAngle = verticalAngle;
        this.percentArea = percentArea;
        this.skew = skew;
        this.boundary = boundary;
    }

    /**
     * Get the bounding box of the target.
     * @return The bounding box.
     */
    public RotatedRect getBoundary() {
        return boundary;
    }

    /**
     * Get the horizontal angle from the center of the camera to the center of the target in degrees.
     * @return The horizontal angle.
     */
    public double getHorizontalAngle() {
        return horizontalAngle;
    }

    /**
     * Get the vertical angle from the center of the camera to the center of the target in degrees.
     * @return The vertical angle.
     */
    public double getVerticalAngle() {
        return verticalAngle;
    }

    /**
     * Get the percent area of the target compared to the image in percentage.
     * @return The percent area.
     */
    public double getPercentArea() {
        return percentArea;
    }

    /**
     * Get the skew of the target in degrees, from -90 to 90 where negative values are angled to the left.
     * @return The skew in degrees.
     */
    public double getSkew() {
        return skew;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Target target = (Target) o;
        return Double.compare(target.horizontalAngle, horizontalAngle) == 0 &&
                Double.compare(target.verticalAngle, verticalAngle) == 0 &&
                Double.compare(target.percentArea, percentArea) == 0 &&
                Double.compare(target.skew, skew) == 0 &&
                Objects.equals(boundary, target.boundary);
    }

    @Override
    public int hashCode() {
        return Objects.hash(horizontalAngle, verticalAngle, percentArea, skew, boundary);
    }

    @Override
    public String toString() {
        return "Target{" +
                "horizontalAngle=" + horizontalAngle +
                ", verticalAngle=" + verticalAngle +
                ", percentArea=" + percentArea +
                ", skew=" + skew +
                ", boundary=" + boundary +
                '}';
    }
}
```
   
## Connecting to a Raspberry Pi

## Finding Angles

## Motor control

##
##
