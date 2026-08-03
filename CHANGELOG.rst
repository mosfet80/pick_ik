^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package pick_ik
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1.1.3 (2026-08-03)
------------------
* Migrate from tl_expected to libexpected-dev system package (`#81 <https://github.com/PickNikRobotics/pick_ik/issues/81>`_)
  ``cpp_polyfills`` 2.0 dropped its ``tl_expected`` sub-package, so the
  ``tl_expected`` rosdep key no longer resolves on Ubuntu Resolute. Depend on
  ``libexpected-dev`` instead, which is available on jammy, noble and resolute
  alike. Required for lyrical and rolling.
* Rolling/lyrical: tf2 .hpp header renames + pick_ik include prefix (`#82 <https://github.com/PickNikRobotics/pick_ik/issues/82>`_)
* ci: switch from custom-container CI to industrial_ci (`#83 <https://github.com/PickNikRobotics/pick_ik/issues/83>`_)
  The pre-baked CI container was frozen at its 2023-12 build and its weekly
  rebuild had been failing and then auto-disabled, so every PR for the past two
  years was tested against an environment that no longer exists. industrial_ci
  installs dependencies fresh per run and follows each distro's current base OS,
  matching the buildfarm and the rest of the MoveIt/PickNik release matrix.
  Rolling now builds against ``ros2-testing`` on Resolute, and ``git`` is
  declared as a ``test_depend`` for the Catch2 ``FetchContent`` step.
* Contributors: LarsNobleo, Nathan Brooks

1.1.2 (2026-06-26)
------------------
* Adds header file for pick_ik_plugin (`#79 <https://github.com/PickNikRobotics/pick_ik/issues/79>`_)
* Contributors: Mark Johnson

1.1.1 (2024-11-30)
------------------
* Initialize with the best seed instead of initial seed at population wipeout (`#77 <https://github.com/PickNikRobotics/pick_ik/issues/77>`_)
* Fix timeout calculation if solution callback fails (`#73 <https://github.com/PickNikRobotics/pick_ik/issues/73>`_)
* Remove incorrect override of tip_frames (`#68 <https://github.com/PickNikRobotics/pick_ik/issues/68>`_)
* Contributors: Amal Nanavati, Sebastian Castro, Timon Engelke

1.1.0 (2023-12-13)
------------------
* Support continuous (unbounded) joints properly (`#59 <https://github.com/PickNikRobotics/pick_ik/pull/59>`_)
* Run elite gradient descent in separate threads (`#61 <https://github.com/PickNikRobotics/pick_ik/pull/61>`_)
* Contributors: Sebastian Castro

1.0.2 (2023-07-25)
------------------
* New options to control solution quality and performance
   * Option to rerun optimization until valid solution or timeout (`#53 <https://github.com/PickNikRobotics/pick_ik/pull/53>`_)
   * Option to keep optimizing after a valid solution was found (`#46 <https://github.com/PickNikRobotics/pick_ik/pull/46>`_)
   * Approximate solution cost threshold (`#51 <https://github.com/PickNikRobotics/pick_ik/pull/51>`_) and joint jump threshold parameters (`#42 <https://github.com/PickNikRobotics/pick_ik/pull/42>`_)
   * Position scale parameter (`#47 <https://github.com/PickNikRobotics/pick_ik/pull/47>`_)
* Fix ordering of joint limits when loading robot model (`#54 <https://github.com/PickNikRobotics/pick_ik/pull/54>`_)
* Fix use of solution callback (`#48 <https://github.com/PickNikRobotics/pick_ik/pull/48>`_)
* Remove unnecessary preprocessor macro (`#40 <https://github.com/PickNikRobotics/pick_ik/pull/40>`_)
* Contributors: Marc Bestmann, Sebastian Castro, Erik Holum

1.0.1 (2023-03-28)
------------------
* Set Werror through CMake presets (`#39 <https://github.com/PickNikRobotics/pick_ik/issues/39>`_)
* Replace lower_bounds with gt_eq (`#37 <https://github.com/PickNikRobotics/pick_ik/issues/37>`_)
* Upgrade with new pkgs to fix issue with ROS
* Target include subdirectory
* Update Catch2 version to 3.3.0
* Fix overriding of package
* Fix orientation calculation in cost function and frame tests (`#31 <https://github.com/PickNikRobotics/pick_ik/issues/31>`_)
   * Fix orientation calculation
   * Update plugin return values
   * Remove redundant (and incorrect) joints bounds check
   * Use Eigen angular distance calculation
* Small grammar fixes (`#28 <https://github.com/PickNikRobotics/pick_ik/issues/28>`_)
* Contributors: Sebastian Castro, Stephanie Eng, Tyler Weaver

1.0.0 (2022-12-08)
------------------
* pick_ik inverse kinematics plugin compatible with MoveIt 2
* Numeric gradient descent (local) solver
* Memetic algorithm (global solver), configurable for single or multi-threading
* Basic goal functions: joint centering, avoid joint limits, minimal joint displacement
* Support for position-only IK and approximate solutions
* Dynamic parameter switching at runtime using `generate_parameter_library <https://github.com/PickNikRobotics/generate_parameter_library>`_
* Docker devcontainer workflow for VSCode
* Contributors: Chris Thrasher, Sebastian Castro, Tyler Weaver
