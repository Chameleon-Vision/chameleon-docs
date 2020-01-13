.. _robot-code:

Robot Code Example
====================

This example code demonstrates the basics of NetworkTables and vision alignment.

NetworkTables
---------------

This code reads the yaw value to the target from NetworkTables and prints it.
It also puts the camera into Drive Mode when the ``A`` button is pressed on the Joystick.

.. code-block:: java

    import edu.wpi.first.wpilij.TimedRobot;
    import edu.wpi.first.networktables.NetworkTable;
    import edu.wpi.first.networktables.NetworkTableEntry;
    import edu.wpi.first.networktables.NetworkTableInstance;

    public class NetworkTableExampleRobot extends TimedRobot {
        public Joystick joystick;
        public NetworkTableEntry yaw;
        public NetworkTableEntry isDriverMode;

        public void robotInit() {
            // Gets the joystick connected to port 1
            joystick = new Joystick(1);

            // Gets the default instance of NetworkTables
            NetworkTableInstance table = NetworkTableInstance.getDefault();

            // Gets the MyCamName table under the chamelon-vision table
            // MyCamName will vary depending on the name of your camera
            NetworkTable cameraTable = table.getTable("chameleon-vision").getSubTable("MyCamName");

            // Gets the yaw to the target from the cameraTable
            yaw = cameraTable.getEntry("yaw");

            // Gets the driveMode boolean from the cameraTable
            isDriverMode = cameraTable.getEntry("driver_mode");
        }

        public void teleopPeriodic() {
            // Prints the yaw to the target
            System.out.println(yaw.getDouble(0.0));

            // Sets driver mode to true if the A button is pressed
            isDriverMode.setBoolean(joystick.GetRawButton(0));
        }
    }

Vision Alignment
------------------

This is an example written in Java. 
This is an imaginary robot with a drivetrain consisting of four Spark motors and a Joystick in port 1.


.. code-block:: java

    public class Robot extends TimedRobot {
        //Variables
        
        //Robot vars (not directly related to the vision system)
        
        public Joystick joystick;
        
        //This example uses 4 spark motors controllers for the drivetrain with 2 motors on each side
        Spark m_frontLeft;
        Spark m_rearLeft;
        SpeedControllerGroup m_left;

        Spark m_frontRight;
        Spark m_rearRight;
        SpeedControllerGroup m_Right;
        
        DifferentialDrive m_drive;



        /*
        NetworkTable is a collection of databases stored in the RoboRIO
        The co processor can change data inside it
        This database can be viewed in a program named OutlineViewer
        "table" represents a single database called "MyCamName" under "Chameleon Vision`"
        */
        NetworkTable table;

        /*
        targetX represents the horizontal angle
        targetY represents the vertical angle
        */
        NetworkTableEntry targetX; 
        NetworkTableEntry targetY;



        //Error values for the control loop
        double rotationError;
        double distanceError;

        //Control loop constants
        /*
            This example uses proportional control loop with constant force
            After you master proportional control use might want to try PID control loop
        */
        double KpRot=-0.1;
        double KpDist=-0.1;

        //Deadzone is necessary because the robot can only get so accurate and cannot be pefectly head on the target
        double angleTolerance=5;//Deadzone for the angle control loop
        double distanceTolerance=5;//Deadzone for the distance control loop
        
        /*
        There is a minimum power that you need to give to the drivetrain in order to overcome friction
        It helps the robot move and rotate at low speeds
        */
        double constantForce=0.05;

        /*
        rotationAjust is rotational signal for the drivetrain
        distanceAjust is forward signal for the drivetrain
        */
        double rotationAjust;
        double distanceAjust;


        //Initilazition function
        public void robotInit(){
            //Initilazition of robot drivetrain and joystick
            joystick = new Joystick(1);
            m_frontLeft = new Spark(1);
            m_rearLeft = new Spark(2);
            m_left = new SpeedControllerGroup(m_frontLeft, m_rearLeft);
            m_frontRight = new Spark(3);
            m_rearRight = new Spark(4);
            m_Right = new SpeedControllerGroup(m_frontRight, m_rearRight);
        
            m_drive = new DifferentialDrive(m_left, m_right);

            //Points "table" to the NetworkTable database called "chameleon-vision" 
            table=NetworkTableInstance.getDefault().getTable("chameleon-vision").getSubTable("MyCamName");

            //Points to the database value named "yaw" and "pitch"
            targetX=table.getEntry("yaw");
            targetY=table.getEntry("pitch");
        }

        //Periodic function
        public void teleopPeriodic()
        {
            rotationAjust=0;
            distanceAjust=0;
            if (joystick.GetRawButton(0))//the "A" button
            {
                /*
                    Fetches the rotation and distance values from the vision co processor
                    sets the value to 0.0 if the value doesnt exist in the database
                */
                rotationError=targetX.getDouble(0.0);
                distanceError=targetY.getDouble(0.0);

                /*
                    Proportional (to targetX) control loop for rotation
                    Deadzone of angleTolerance
                    Constant power is added to the direction the control loop wants to turn (to overcome friction)
                */
                if(rotationError>angleTolerance)
                    rotationAjust=KpRot*rotationError+constantForce;
                else
                    if(rotationError<angleTolerance)
                        rotationAjust=KpRot*rotationError-constantForce;
                /*
                    Proportional (to targetY) control loop for distance
                    Deadzone of distanceTolerance
                    Constant power is added to the direction the control loop wants to turn (to overcome friction)
                */
                if(distanceError>distanceTolerance)
                    distanceAjust=KpDist*distanceError+constantForce;
                else
                    if(distanceError<distanceTolerance)
                        distanceAjust=KpDist*distanceError-constantForce;

                
                //Output the power signals to a arcade drivetrain
                m_drive.arcadeDrive(distanceAjust,rotationAjust);
            }		
        }
    }

.. labview and c++ maybe?
