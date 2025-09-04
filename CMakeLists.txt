AddProject(biRobotTeleop_utils
  GITHUB antodld/biRobotTeleopTask
  GIT_TAG origin/main
  DEPENDS mc_rtc
)

AddProject(UDPDataLink
  GITHUB antodld/UDPDataLink
  GIT_TAG origin/main
)

AddProject(openvr
  GITHUB ValveSoftware/openvr
  GIT_TAG origin/master
)

AddProject(openVrPlugin
  GITHUB antodld/mc_OpenVR_plugin
  GIT_TAG origin/main
  DEPENDS mc_rtc openvr
  CMAKE_ARGS -DBUILD_TESTING:BOOL=OFF
)

AddProject(joystickPlugin
  GITHUB antodld/mc_joystick_plugin
  GIT_TAG origin/main
  DEPENDS mc_rtc
)

AddProject(contact_estimation
  GITHUB arntanguy/mc_contact_estimation
  GIT_TAG origin/main
  DEPENDS mc_rtc
)

AddCatkinProject(puppet_description
  GITHUB antodld/puppet_description
  GIT_TAG origin/main
  WORKSPACE data_ws
)

AddProject(puppet
  GITHUB antodld/mc_puppet
  GIT_TAG origin/main
  DEPENDS mc_rtc puppet_description
)

AddProject(mc_biRobotTeleop
  # GITHUB antodld/mc_biRobotTeleop
  # GIT_TAG origin/main
  GITHUB arntanguy/mc_biRobotTeleop
  GIT_TAG origin/topic/Upgrade
  DEPENDS mc_rtc biRobotTeleop_utils puppet contact_estimation joystickPlugin openVrPlugin UDPDataLink
)

# Human model
AddCatkinProject(human_description
  GITHUB jrl-umi3218/human_description
  GIT_TAG origin/master
  WORKSPACE data_ws
)

AddProject(mc_human
  GITHUB jrl-umi3218/mc_human
  GIT_TAG origin/master
  DEPENDS human_description mc_rtc
)

