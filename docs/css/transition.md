# transition 过渡

provide a way to control animation speed when changing CSS properties

- 指定某个属性从一个状态到另一个状态时如何过渡
- 动画的意义: 告诉用户发生了什么
- transition属性
  - `transition-property`
  - `transition-duration`
  - `transition-timing-function`
    - linear 线性
    - ease 
    - ease-in
    - ease-out
    - ease-in-out
    - steps(4)
  - `transition-delay`

## 语法

```css
transition: transition-property transition-duration transition-timing-function transition-delay
```