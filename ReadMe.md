# Introduction
An example netty based http server, that can be compiled to a native binary image using graalvm's native-image.

# Quickstart
1. Download GraalVM and extract it to somewhere. Then set the `JAVA_HOME` environment variable to the home of it.
2. Run `mvn package` on the root directory of this project.
3. The native image is produced under `target` directory. So you could run it to start the example server.
4. Open the [link](http://localhost:9000) and enjoy it.

# Issues
- When the output server is run, the logging handler should print to console something like the following.
    > Jul 18, 2019 2:49:09 PM io.netty.handler.logging.LoggingHandler channelRegistered
      INFO: [id: 0x45e23bb2] REGISTERED
      Jul 18, 2019 2:49:09 PM io.netty.handler.logging.LoggingHandler bind
      INFO: [id: 0x45e23bb2] BIND: 0.0.0.0/0.0.0.0:9000
      Server started, will shutdown now.
      Jul 18, 2019 2:49:09 PM io.netty.handler.logging.LoggingHandler channelActive
      INFO: [id: 0x45e23bb2, L:/0:0:0:0:0:0:0:0:9000] ACTIVE
  
  But sometimes the output server image does not log the above output, even though the native-image settings has not
  changed. Still wonder why. 