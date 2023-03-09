# http4s-grpc

A pure Scala [gRPC] implementation! Use it with [http4s Ember] and deploy on JVM, Node.js, and Native.

The generated APIs use Cats Effect and FS2, and are nearly drop-in replacements for code generated by [fs2-grpc].

[gRPC]: https://grpc.io/
[http4s Ember]: https://http4s.org/v0.23/docs/integrations.html#ember
[fs2-grpc]: https://github.com/typelevel/fs2-grpc

## Quick Start

First add the plugin to `project/plugins.sbt`.

```scala
addSbtPlugin("io.chrisdavenport" % "sbt-http4s-grpc" % "0.0.1")
```

Then in your `build.sbt` enable the `Http4sGrpcPlugin` to configure the http4s-grpc codegen. In addition, you will need to configure the [ScalaPB] codegen by following their [installation docs][ScalaPB installation].

```scala
enablePlugins(Http4sGrpcPlugin)
Compile / PB.targets ++= Seq(
  // set grpc = false because http4s-grpc generates its own code
  scalapb.gen(grpc = false) -> (Compile / sourceManaged).value / "scalapb"
)
```

[ScalaPB]: https://scalapb.github.io/
[ScalaPB installation]: https://scalapb.github.io/docs/installation
