# 2026 KitBot Code

Robot code for the [2026 FRC KitBot](https://www.firstinspires.org/robotics/frc/kitbot), built with WPILib and the command-based framework. This project controls a differential-drive robot with a fuel intake and launcher mechanism using REV Spark Max motor controllers.

## Requirements

- [WPILib 2026](https://docs.wpilib.org/) (install via the [WPILib installer](https://github.com/wpilibsuite/allwpilib/releases))
- Java 17
- VS Code with the WPILib extension (recommended)

## Project Structure

```
src/main/java/frc/robot/
├── Main.java              # Entry point
├── Robot.java             # Robot lifecycle and command scheduler
├── RobotContainer.java    # Subsystems, bindings, and auto chooser
├── Constants.java         # Motor IDs, voltages, and tuning values
├── commands/
│   └── Autos.java         # Autonomous routines
└── subsystems/
    ├── CANDriveSubsystem.java   # Differential drive
    └── CANFuelSubsystem.java    # Intake / launch mechanism
```

## Hardware

### Drivetrain (`CANDriveSubsystem`)

| Motor            | CAN ID |
|------------------|--------|
| Left leader      | 10     |
| Left follower    | 11     |
| Right leader     | 9      |
| Right follower   | 8      |

Four brushed Spark Max controllers in a differential drive configuration. Followers track their respective leaders. The left side is inverted so positive values drive both sides forward.

### Fuel Mechanism (`CANFuelSubsystem`)

| Motor              | CAN ID |
|--------------------|--------|
| Intake / launcher  | 12     |
| Feeder             | 19     |

Two brushed Spark Max controllers run the intake roller and feeder roller. Motor voltages are tunable from the SmartDashboard at runtime.

## Controls

The operator uses an Xbox controller on **USB port 0** (see `Constants.OperatorConstants`).

| Input              | Action                                      |
|--------------------|---------------------------------------------|
| Left stick Y       | Drive forward / reverse                     |
| Right stick X      | Turn in place                               |
| Left bumper        | Intake fuel                                 |
| Right bumper       | Spin up (1 s), then launch                  |
| A button           | Eject fuel out the intake                   |
| B button           | Launch at alternate speed (second bot)      |

Drive and rotation inputs are scaled to 70% and 80% respectively for easier control.

## Autonomous

The default autonomous routine (`Autos.exampleAuto`):

1. Drive backward for 0.25 seconds
2. Stop driving
3. Spin up the launcher for 1 second
4. Launch fuel for 9 seconds
5. Stop the launcher

Select routines from the SmartDashboard auto chooser. Add more options in `RobotContainer` with `autoChooser.addOption(...)`.

## Tuning

Fuel mechanism voltages live in `Constants.FuelConstants` and are also exposed on the SmartDashboard:

- Intaking feeder / intake roller voltages
- Launching feeder / launcher roller voltages
- Spin-up feeder roller voltage and duration

Tune on the dashboard during practice, then copy the values back into `Constants.java` for consistent behavior.

## Build and Deploy

### Build

```bash
./gradlew build
```

### Deploy to roboRIO

1. Set your team number in `.wpilib/wpilib_preferences.json` (currently **21301**), or pass it on the command line.
2. Connect the robot to the same network as your development machine.
3. Deploy from VS Code (**WPILib: Deploy Robot Code**) or from the terminal:

```bash
./gradlew deploy
```

### Simulation

Simulation GUI and Driver Station integration are enabled in `build.gradle`. Run simulation from VS Code with **WPILib: Simulate Robot Code on Desktop**.

## Dependencies

| Library   | Version  |
|-----------|----------|
| GradleRIO | 2026.2.1 |
| REVLib    | 2026.0.5 |

## License

This project uses WPILib, which is licensed under the BSD 3-Clause License. See [WPILib-License.md](WPILib-License.md) for details.
