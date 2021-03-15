RidgeRun's GSCam

Forked from: [GSCam project](https://github.com/ros-drivers/gscam)
===========================================================================================================================

GStreamer Support
-------------------------

GScam supports GStreamer 1.0

#### Dependencies:
 
* gstreamer1.0-tools 
* libgstreamer1.0-dev 
* libgstreamer-plugins-base1.0-dev 
* libgstreamer-plugins-good1.0-dev

Ubuntu Installation:

```sh
sudo apt-get install gstreamer1.0-tools libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev
```

#### Usage:
* See the [Video4Linux2 launchfile example](examples/v4l.launch) for
  an example of the differences in the GStreamer config lines

#### Notes:
* This has been tested with `v4l2src` and [GStreamer Daemon](https://developer.ridgerun.com/wiki/index.php?title=GStreamer_Daemon_-_ROS) 

ROS API (stable)
----------------

### gscam

This can be run as both a node and a nodelet.

#### Nodes
* `gscam`

#### Topics
* `camera/image_raw`
* `camera/camera_info`

#### Services
* `camera/set_camera_info`

#### Parameters
* `~camera_name`: The name of the camera (corrsponding to the camera info)
* `~camera_info_url`: A url (`file://path/to/file`, `package://pkg_name/path/to/file`) to the [camera calibration file](http://www.ros.org/wiki/camera_calibration_parsers#File_formats).
* `~gscam_config`: The GStreamer [configuration string](http://wiki.oz9aec.net/index.php?title=Gstreamer_cheat_sheet&oldid=1829).
* `~frame_id`: The [TF](http://www.ros.org/wiki/tf) frame ID.
* `~reopen_on_eof`: Re-open the stream if it ends (EOF).
* `~sync_sink`: Synchronize the app sink (sometimes setting this to `false` can resolve problems with sub-par framerates).


Examples
--------

See example launchfiles and configs in the examples directory. Currently there
are examples for:

* [GStreamer Daemon](examples/gstd-demo.launch): ROS + GstD Demo
* [Video4Linux2](examples/v4l.launch): Standard
  [video4linux](http://en.wikipedia.org/wiki/Video4Linux)-based cameras like
  USB webcams.
    * ***GST-1.0:*** Use the roslaunch argument `GST10:=True` for GStreamer 1.0 variant
* [Nodelet](examples/gscam_nodelet.launch): Run a V4L-based camera in a nodelet
* [Video File](examples/videofile.launch): Any videofile readable by GStreamer
* [DeckLink](examples/decklink.launch):
  [BlackMagic](http://www.blackmagicdesign.com/products/decklink/models)
  DeckLink SDI capture cards (note: this requires the `gst-plugins-bad` plugins)
