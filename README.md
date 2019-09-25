# LearningOpenCV - Depricated (For Now)
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
3. Run as a **Gradle** project
4. Hold up the vision target in the cameras range of sight

=================================================================================

### Bugs
Currently, I know that there is one issue in `Scannable.java` that throws an IOException probably because I have not implamented the class properly

### Sources
Java 11, OpenCV

# Docs
**Note** the code in this repo demonstrates how to use OpenCV and Java for the 2018-2019 FIRST Robotics Compitition.

## Camera

   ### Setting the Camera Input Port
   
   ### Sending the output to a Server

## Target
   
   ### Combining The Objects
   
   ### Setting the target
   So technically `ContourToTargetConverter.java` converts the vision tape into a target, but `RectToTargetHelper.java` does the most work. So in [RectToTargetHelper.java](/src/main/java/com/RidleyNelson17/lib/vision/targetConverters/RectToTargetHelper.java) 
   
   ```
   class RectToTargetHelper {
      private final double cameraWidth;
      private final double cameraHeight;
      private final double vpw;
      private final double vph;
      private final double imageArea;

      public RectToTargetHelper(CameraSettings cameraSettings){
         cameraWidth = cameraSettings.getResolution().getWidth();
         cameraHeight = cameraSettings.getResolution().getHeight();

         double horizontalFOV = Math.toRadians(cameraSettings.getFov().getHorizontalDegrees());
         double verticalFOV = Math.toRadians(cameraSettings.getFov().getVerticalDegrees());

         vpw = 2.0 * Math.tan(horizontalFOV / 2.0);
         vph = 2.0 * Math.tan(verticalFOV / 2.0);

         imageArea = cameraWidth * cameraHeight;
      }

      public Target convertRectToTarget(RotatedRect boundary){
         double nx = (2.0 / cameraWidth) * (boundary.center.x - cameraWidth / 2.0 - 0.5);
         double ny = (2.0 / cameraHeight) * (boundary.center.y - cameraHeight / 2.0 - 0.5);
         double x = vpw / 2.0 * nx;
         double y = vph / 2.0 * ny;
         
         double horizontalAngle = Math.toDegrees(Math.atan(x));
         double verticalAngle = -Math.toDegrees(Math.atan(y));
         
         double percentArea = boundary.size.area() / imageArea * 100.0;
         double skew = boundary.angle;
         if (boundary.size.width < boundary.size.height){
            skew = 90 + boundary.angle;
         }
         
         return new Target(horizontalAngle, verticalAngle, percentArea, skew, boundary);
      }
   }
   ```
   
## Connecting to a Raspberry Pi

## Finding Angles

## Motor control

##
##
