.. _robot-code:

Robot code example
===================

Read this example code to understand the `idea` and `concepts` of networktables and vision alignment

How to read and write to Networktables
-----------------------------------------

This example code reads if the `A` button on joystick 1 is pressed and puts it in driver mode so when `A` is pressed driver mode will be enabled

Also the code will print periodically the yaw angle(horizontal angle). 

.. code-block:: java

	public class Robot extends IterativeRobot {

		public Joystick joystick;
		public NetworkTableEntry yaw;
		public NetworkTableEntry isDriverMode;

		public void robotInit(){
			joystick = new Joystick(1);
			NetworkTableInstance table = NetworkTableInstance.getDefault();
			NetworkTable myCam = table.getTable("chameleon-vision").getSubTable("MyCamName");
			yaw=myCam.getEntry("yaw");
			isDriverMode=myCam.getEntry("driver_mode");
		}

		//Periodic function
		public void teleopPeriodic()
		{
			System.out.println(yaw.getDouble(0.0));//trys to print yaw, if it doesnt exist it will print 0
			isDriverMode.setBoolean(joystick.GetRawButton(0));//sets driver mode to true if A is pressed
		}
	}

Vision align and drive code example
------------------------------------
| This is an example code in `Java` so you can understand how to implement Chameleon Vision in your code.
| Is a one class, iterative robot that is written as an example, please write a command based code as your main code.

| 
| This imaginary robot has 4 spark motors in the drivetrain.
| 2 motors in each side 
| Left: 1,2 Right: 3,4
| Joystick controller in port 1
| the kP values need to be adjusted for your robot and vision needs

.. code-block:: java

	public class Robot extends IterativeRobot {
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
