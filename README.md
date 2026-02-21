# ANYmal Simulator Workaround

Fix for ANYmal Appearing Underground in Simulation

Some users of the ANYbotics ANYmal simulator encounter an issue where the robot appears underground when launching the simulation.

This guide explains a simple workaround to fix that behavior.

---

## Problem

When launching the ANYmal simulator, the robot may appear below the ground plane instead of properly standing in the environment.

If your simulation looks normal, you can ignore this guide.
If the robot appears underground, follow the steps below.

---

## Steps to Fix

### 1. Install ANYmal Simulator

Download and install the simulator from the official documentation:

[https://anymal-research.docs.anymal.com/user_manual/anymal_d100_operators_manual-workforce_app/release-25.06/html/Operators_Manual/Getting_started/ANYmal_Software_Installer__ASI_/New_topics/Install_the_GUI_and_simulation.htm](https://anymal-research.docs.anymal.com/user_manual/anymal_d100_operators_manual-workforce_app/release-25.06/html/Operators_Manual/Getting_started/ANYmal_Software_Installer__ASI_/New_topics/Install_the_GUI_and_simulation.htm)

---

### 2. Launch the ANYmal Simulator

Open the simulator normally.

* If the robot appears correctly → stop here.
* If the robot appears underground → continue.

---

### 3. Enter the Simulation Docker Container

Open a terminal and run:

```bash
sudo docker exec -ti any-simulation-environment-1 bash
```

---

### 4. Launch Gazebo Client

Inside the container, run:

```bash
gzclient
```

This opens the Gazebo GUI.

---

### 5. Add the Playground Model Path

In Gazebo:

1. Go to the **Insert** tab.
2. Click **Add Path**.
3. Navigate to:

```
/opt/ros/noetic/share/playground_data/models
```

4. Click **Choose**.

---

### 6. Prevent Accidental Simulation Interaction

1. Click on **World** in the left panel.
2. At the top toolbar, click the **selection/arrow tool icon** (important).

   This prevents objects from moving with your cursor.

   If you accidentally move something:

   * Click **World** again to reset selection.

---

### 7. Verify the Simulation

You should now see a clean simulation environment in Gazebo with ANYmal properly positioned.

---

### 8. Control ANYmal

Return to the ANYmal GUI and control the robot normally.

You should now see the robot moving correctly inside the Gazebo simulation.

---

## Notes

* This is a workaround for a visualization/environment loading issue.
* It does not modify core simulation files.
* If the problem persists, restarting the container may help.
