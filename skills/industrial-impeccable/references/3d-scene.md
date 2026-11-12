# C 族 · 3D 场景（three.js，机器人单元可视化）

> 底本：cesartevisual/threejs-skills spatial-data + performance（MIT）。

## 坐标三铁律

1. **源坐标与渲染坐标分离**：车间/全局坐标与稳定标识符（件号/腔位号）一组；渲染坐标另一组；之间记录**可逆变换**——拾取、测量、导出、标注必须能映射回源。
2. **局部原点**：渲染原点定在机器人单元中心（非世界原点），保护 float32 精度（大坐标远处抖动）。
3. **up 轴显式转换**：机器人控制器 Z-up（如 AUBO）↔ three.js Y-up，转换写一次、写显式，禁止散落各处。

## 测量与选择

4. 测量预先定义：吸附行为、单位（mm）、公差、值代表变换后还是源几何。
5. 语义选择与绘制批处理分开——合批不得吞掉腔位/部件点击。

## 资源所有权（Vue onUnmounted 清单）

6. 谁拥有谁释放：geometry / material / texture / render target / controls / mixer / observer / 事件监听。
7. 三个"不会自动"：dispose 材质不会释放纹理；dispose 渲染器不会释放场景对象；共享缓存条目（loader 缓存）不许删。
8. 测漏看趋势：反复挂载/卸载后看"不明原因上升"，不苛求绝对零。

## 性能

9. 先诊断后动刀：分瓶颈类型（draw calls→实例化；填充→降 overdraw；CPU→避免每帧分配与重复着色器编译）；**降三角形不治所有瓶颈**；一次只改一个大变量，测前后值。

## 验收

坐标往返抽测（源→渲染→源一致）；卸载 N 次无泄漏上升趋势。

## 出处

cesartevisual/threejs-skills（MIT）。
