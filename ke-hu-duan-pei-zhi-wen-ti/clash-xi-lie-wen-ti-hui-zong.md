# Clash 系列问题汇总

## 无法使用、代理未生效

1. 请确认 Clash 的系统代理开关是否开启
   * macOS 下的 ClashX 开启方法为，点击 ClashX 状态栏图标，勾选「设置为系统代理」
   * Windows 下 Clash for Windows 开启方法为 General 页面打开「System Proxy」开关

## 添加订阅失败

1. 还请验证是否在没有配置完成的情况下打开了 Clash 的系统代理。
   * 在没有配置完成或者套餐过期后，打开系统代理会导致 Clash 添加、更新订阅也走代理线路，此时代理线路处于未配置或套餐过期的状态，导致添加、更新订阅失败。