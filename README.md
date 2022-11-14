# Cyber-Physical Systems Testing Tool Competition #

The [SBFT Workshop](https://sbft23.github.io/) offers a challenge for software testers who want to work with self-driving cars in the context of the usual [tool competition](https://sbft23.github.io/tools/).

## Important Dates

The deadline to submit your tool is: **January 13st 2023**

The results of the evaluation will be communicated to participants on: **February 24th 2023**

The camera-ready paper describing your tool is due to: **March 17th 2023**

## Goal ##
The competitors should generate virtual roads to test a lane keeping assist system using the provided code pipeline. The aim of the generation is falsification: the roads produced should make the lane keeping assist system drive out of the lane. The ranking of the tools is based on coverage which measures the number of failed tests and their quality. We do this as it is in the interest of any system tester to provide as diverse failures as possible. This facilitates better root cause analysis. 

The generated roads are evaluated in the [**BeamNG.tech**](https://www.beamng.tech/) driving simulator.
This simulator is ideal for researchers due to its state-of-the-art soft-body physics simulation, ease of access to sensory data, and a Python API to control the simulation.

In the competition two lane keeping assists are used: BeamnNG.AI provided by the BeamnNG.tech simulator and DAVE-2 trained by the competition organizers.

[![Video by BeamNg GmbH](https://github.com/BeamNG/BeamNGpy/raw/master/media/steering.gif)](https://github.com/BeamNG/BeamNGpy/raw/master/media/steering.gif)

>Note: BeamNG GmbH, the company developing the simulator, kindly offers it for free for researcher purposes upon registration (see [Installation](documentation/INSTALL.md)).

## Comparing the Test Generators ##

Deciding which test generator is the best is far from trivial and, currently, remains an open challenge. In the 2023 instance of the competition, we rank the test generators according to a coverage metric. This means that we select relevant features, build a feature map for them, and compute how much each tool covers this map. Possible features to be used include
* Direction Coverage (DirCov).
* Standard Deviation of the Steering Angle (StdSA).
* Maximum Curvature (MaxCurv).
* Mean Lateral Position (MLP).

We expect that the submitted tools are stochastic in nature, so we compute the coverage as the total coverage over several repetitions of the tool.

## Implement Your Test Generator ##
We make available a [code pipeline](code_pipeline) that will integrate your test generator with the simulator by validating, executing and evaluating your test cases. Moreover, we offer some [sample test generators](sample_test_generators/README.md) to show how to use our code pipeline.

## Information About the Competition ##
More information can be found on the SBFT tool competition website: [https://sbft23.github.io/tools/](https://sbft23.github.io/tools/) See also the tool report of the previous competition instance: <https://ieeexplore.ieee.org/document/9810771>

## Repository Structure ##
[Code pipeline](code_pipeline): code that integrates your test generator with the simulator.

[Self driving car testing library](self_driving): library that helps the integration of the test input generators, our code pipeline, and the BeamNG simulator.

[Scenario template](levels_template/tig): basic scenario used in this competition.

[Documentation](documentation/README.md): contains the installation guide, detailed rules of the competition, and the frequently asked questions.

[Sample test generators](sample_test_generators/README.md): sample test generators already integrated with the code pipeline for illustrative purposes.

[Requirements](requirements.txt): contains the list of the required packages.


## License ##
The software we developed is distributed under GNU GPL license. See the [LICENSE.md](LICENSE.md) file.

## Contacts ##

Dr. Alessio Gambi  - Passau University, Germany - alessio.gambi@uni-passau.de

Dr. Vincenzo Riccio  - Universita' della Svizzera Italiana, Lugano, Switzerland - vincenzo.riccio@usi.ch
