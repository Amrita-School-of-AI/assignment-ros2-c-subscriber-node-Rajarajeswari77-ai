cmake_minimum_required(VERSION 3.8)
project(ros2_subscriber)

# Enable extra compiler warnings for GCC/Clang
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find required packages
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

# Create the subscriber executable
add_executable(subscriber_node src/subscriber_node.cpp)

# Link dependencies
ament_target_dependencies(subscriber_node
  rclcpp
  std_msgs
)

# Install the executable
install(TARGETS
  subscriber_node
  DESTINATION lib/${PROJECT_NAME}
)

# Testing (optional but standard)
if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()


