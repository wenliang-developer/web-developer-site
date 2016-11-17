WebGL 1.0 是以 OpenGL ES 2.0 为蓝本设计的，OpenGL ES 2.0 则是以 OpenGL 2.0 为蓝本设计的。所以，别看表面上跑的是 JavaScript，真正运行的时候还是跑在 OpenGL 驱动上的（Windows平台是例外，可以使用 Direct3D 9 / 11 来模拟的 WebGL）。
你要想真正学会 WebGL，必须得懂 OpenGL 和图形学，以及 shader 语言。
当然了，由于 Three.js 这类游戏引擎的存在，即便你不懂 WebGL，也可以快速地进行开发，但是，一旦你遇到意料之外的问题了，还是得回过头来看 WebGL，甚至看 OpenGL 红宝书。

如果要学习传统的 OpenGL，那么脱不了三本书：
- 红宝书 [OpenGL Programming Guide](http://www.glprogramming.com/red/)，出到第八版
- 蓝宝书 [OpenGL SuperBible](http://www.starstonesoftware.com/OpenGL/)，出到第七版
- 橙宝书 [OpenGL Shading Language](http://www.amazon.com/OpenGL-Shading-Language-3rd-Edition/dp/0321637631)，出到第三版

Edward Tufte
