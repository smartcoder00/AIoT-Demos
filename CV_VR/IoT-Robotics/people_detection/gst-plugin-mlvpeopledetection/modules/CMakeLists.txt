# GStreamer ML video detection plugin modules.

# YOLO-NAS
set(GST_QTI_ML_MODULE ml-vdetection-yolo-nas)

add_library(${GST_QTI_ML_MODULE} SHARED
  ml-vdetection-yolo-nas.c
)

target_include_directories(${GST_QTI_ML_MODULE} PUBLIC
  ${GST_INCLUDE_DIRS}
)

target_link_libraries(${GST_QTI_ML_MODULE} PRIVATE
  ${GST_LIBRARIES}
  gstqtimlbase
  gstqtiutilsbase
)

install(
  TARGETS ${GST_QTI_ML_MODULE}
  LIBRARY DESTINATION ${GST_PLUGINS_QTI_OSS_INSTALL_LIBDIR}/gstreamer-1.0/ml/modules
  PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ
            GROUP_EXECUTE GROUP_READ
            WORLD_EXECUTE WORLD_READ
)

# YOLOv8
set(GST_QTI_ML_MODULE ml-vdetection-yolov8)

add_library(${GST_QTI_ML_MODULE} SHARED
  ml-vdetection-yolov8.c
)

target_include_directories(${GST_QTI_ML_MODULE} PUBLIC
  ${GST_INCLUDE_DIRS}
)

target_link_libraries(${GST_QTI_ML_MODULE} PRIVATE
  ${GST_LIBRARIES}
  gstqtimlbase
  gstqtiutilsbase
)

install(
  TARGETS ${GST_QTI_ML_MODULE}
  LIBRARY DESTINATION ${GST_PLUGINS_QTI_OSS_INSTALL_LIBDIR}/gstreamer-1.0/ml/modules
  PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ
            GROUP_EXECUTE GROUP_READ
            WORLD_EXECUTE WORLD_READ
)

# END of GStreamer ML person detection plugin module
