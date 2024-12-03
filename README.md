# nodehub-x5-rdkmodelzoo-samples
包名统一采用nodehub开头：nodehub-x5-rdkmodelzoo-samples

下载RDK Model Zoo的打包仓库
```bash
git clone --recurse-submodules https://github.com/D-Robotics/nodehub-x5-rdkmodelzoo-samples.git
# 如果clone中断
cd nodehub-x5-rdkmodelzoo-samples
git submodule update --init --recursive
```
这个打包仓库按照debian的格式创建，其中Model Zoo的文件夹挂载rdk_model_zoo仓库为子仓库
```bash
nodehub-x5-rdkmodelzoo-samples/
└── debian
    ├── DEBIAN
    └── rdk_model_zoo # 这个是子仓库, 安装deb包后就会在板卡的 /rdk_model_zoo 文件夹
```

进入rdk_model_zoo的子文件夹，对rdk_model_zoo仓库里面的内容进行同步和更新
```bash
cd nodehub-x5-rdkmodelzoo-samples/debian/rdk_model_zoo/
git pull origin main
```

打包的基本命令
```bash
cd ../../. # 确保在nodehub-x5-rdkmodelzoo-samples目录
sudo dpkg -b debian nodehub-x5-rdkmodelzoo-samples_1.0.0_arm64.deb
```

安装这个deb包进行测试
```bash
sudo dpkg -i nodehub-x5-rdkmodelzoo-samples_1.0.0_arm64.deb
```

使用apt查看包的安装状态
```bash
sudo apt show nodehub-x5-rdkmodelzoo-samples
```

卸载deb包
```bash
sudo apt remove nodehub-x5-rdkmodelzoo-samples
```