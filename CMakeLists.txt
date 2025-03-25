cmake_minimum_required(VERSION 3.10.2)
project(heron_msgs)

set(MSG_DEPS
  std_msgs
  actionlib_msgs
  nav_msgs 
  sensor_msgs
  geometry_msgs
  robotnik_msgs
)

find_package(catkin REQUIRED COMPONENTS message_generation ${MSG_DEPS})

set(MSG_FILES
  ConesStatus.msg
)

set(SRV_FILES
  SetNamedCone.srv
  ActionCone.srv
  SpawnObject.srv
  SetConstraint.srv
  GetConePose.srv
  FindCrack.srv
  FindLaneEdge.srv
  FindPothole.srv
  ChangeRobotMode.srv
  TransformPose.srv
  GetDepositSeq.srv
  FindOffset.srv
  GetSynchedImages.srv
  SendImageToKafka.srv
  FindCrackPath.srv
)

set(ACT_FILES
  PickupFrom.action
  PlaceOn.action
  InitHolder.action
  MoveTo.action
  MoveToPose.action
)

add_action_files(DIRECTORY action FILES ${ACT_FILES})
add_message_files(DIRECTORY msg FILES ${MSG_FILES})
add_service_files(DIRECTORY srv FILES ${SRV_FILES})

generate_messages(DEPENDENCIES ${MSG_DEPS})

catkin_package(CATKIN_DEPENDS message_runtime ${MSG_DEPS})
