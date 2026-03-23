# UI-OneForAll
带有UI的OneForAll，支持py3.13

# 使用前加载依赖
cd OneForAll/
python3 -m pip install -U pip setuptools wheel -i https://mirrors.aliyun.com/pypi/simple/
pip3 install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/
python3 oneforall.py --help

# UI版本和命令版本的使用
python3 ui.py
python3 oneforall.py --target example.com run
python3 oneforall.py --targets ./example.txt run

# 本次更新-2026-03-23
本次围绕 Python 3.13 和项目可用性，主要做了这几类更新。

Python 3.13 兼容优化：
- 把 /OneForAll/common/utils.py) 里对 `distutils.version.LooseVersion` 的依赖去掉了，改成 `sys.version_info`，因为 `distutils` 在 Python 3.12+ 已移除。
- 新增了 [`pipes.py`]兼容层，解决旧版 `python-fire` 在 Python 3.13 下因 `pipes` 模块删除而启动失败的问题。
- 把 [`oneforall.py`]/OneForAll/oneforall.py)、[`brute.py`]/OneForAll/brute.py)、[`export.py`]/OneForAll/export.py)、[`takeover.py`]/OneForAll/takeover.py) 里的 `fire` 改成延迟导入，避免普通导入阶段直接报错。
- 更新了 [`requirements.txt`]和 [`Pipfile`]里的相关依赖声明与 Python 版本说明。

新增 UI 界面：
- 新增桌面界面入口 [`ui.py`]，基于 `tkinter`，保留原核心扫描逻辑不变。
- 新增服务层 [`ui_service.py`]，用于把现有 CLI 流程安全复用到 GUI。
- UI 支持目标输入、批量文件、功能开关、实时日志、结果列表、详情查看。
- 结果列表现在支持双击或按钮直接打开目标站点。

文档统一更新：(/Users/hedysx/Downloads/OneForAll/docs/en-us/README.md)。
- 同步修正了 [`docs/usage_help.md`]和 [`docs/en-us/usage_help.md`]。
- 清理了旧文件名、旧参数名、旧路径说明，并把 GUI、Python 3.13 支持状态写进文档。
- 顺手更新了 [`docs/directory_structure.md`]、[`docs/troubleshooting.md`]、[`docs/todo.md`]。
