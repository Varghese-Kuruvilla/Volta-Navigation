<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->




<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/Varghese-Kuruvilla/Volta-Navigation">

<h3 align="center">Point to point Navigation using the volta </h3>

  <p align="center">
    <a href="https://github.com/Varghese-Kuruvilla/Volta-Navigation"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/Varghese-Kuruvilla/Volta-Navigation">View Demo</a>
    ·
    <a href="https://github.com/Varghese-Kuruvilla/Volta-Navigation/issues">Report Bug</a>
    ·
    <a href="https://github.com/Varghese-Kuruvilla/Volta-Navigation/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#known issues">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
Codebase for performing autonomous navigation with the volta. The navigation goals can be given to the robot with the help of the webapp which has been added as a submodule.

**NOTE:**  This project was made specifically for the demo, however it can be used for any scenario where point to point autonomous navigation is required.

<p align="right">(<a href="#top">back to top</a>)</p>





<!-- GETTING STARTED -->
## Getting Started


### Prerequisites

This project has to be cloned on the Xavier which is on the volta. The codebase requires Ubuntu 18.04 + ROS1 melodic (the Xavier on the volta normally has this configuration). 

### Installation
1. Create a ROS1 workspace \
  [Creating a catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace)

2. Clone the repository inside the source folder of the workspace
  ```
  https://github.com/Varghese-Kuruvilla/Volta-Navigation.git

  ```
3. Install the required packages
  ```
  rosdep install --from-paths src --ignore-src -r -y
  ```

**NOTE:** The volta_hardware package hasn't been included in this repository since the code is proprietary. The Xavier should already contain this folder and this should be added to the source folder of the workspace.

4. Build the workspace and source the setup file
```
catkin build
source devel/setup.bash
```
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage
1. Follow the instructions on the webapp-interface repository (demo branch) to launch the webapp. 

2. Bringup the robot:
```
roslaunch volta_base bringup.launch
```
On successful bringup, lights on either side of the volta should glow green.Point 1 of the Known Issues section addresses the most common reason for the failure of bringup.

3. Launch the sensors(Currently we are using only the rplidar):
```
roslaunch volta_base sensors.launch
```

4. Launch the node which performs point to point navigation(It directly accepts goals from the webapp)
```
roslaunch autonomy send_goals.launch
```

5. To teleoperate the volta using the valve controllers:
```
roslaunch teleop_node teleop_node.launch  
```

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Known Issues
1. On startup udev-rules aren't applied properly. As a result the port names **/dev/mcu** and **/dev/rplidar** aren't configured properly. The user might have to manually change the port names on Line 124 of the serialMain.cpp file(located in the volta_hardware folder) and in the sensors.launch file


See the [open issues](https://github.com/Varghese-Kuruvilla/Volta-Navigation/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>
