# ROADMAP

## 当前阶段

已添加并验证 B 站合集中文字幕下载入口；等待用户环境验证实际在线下载。

## 已完成

- 2026-10-04：从 `Simple-Alone/YTSage` 克隆源码，基线为 `80753ad`。
- 已核对合集分析的空字幕列表、前端条件显示和后端字幕参数传递。
- 添加 B 站合集中文字幕选项：空字幕列表时仍可见，默认关闭，复用现有 `subtitle_langs` 字段。
- 同步中英文界面文案及 README 使用说明。
- 前端生产构建通过，本地 Chromium 界面交互和任务请求验证通过。

## 进行中

- 经用户确认，提交并推送字幕入口改动，等待现有 GitHub Actions 测试与镜像发布结果。

## 待办

- Actions 发布成功后，用户切换到本仓库镜像并验证真实 B 站视频与字幕下载。

## 阻塞与待确认

- 本地没有用户的 B 站登录凭据，在线字幕下载结果待用户环境验证。
- 网页播放器加载字幕属于后续独立范围，本次仅添加下载入口。

## 最近验证

- 克隆完成后 `git status --short` 无输出。
- 已确认后端按 `subtitle_langs` 添加 `--write-subs` 与 `--sub-langs`，按 `merge_subtitles` 添加 `--embed-subs`。
- 2026-10-04：`npm --prefix frontend ci`、`npm --prefix frontend run build` 通过。Vite 提示构建包超过 500 kB，该提示不阻断构建，本次未做无关拆包。
- 使用现有 Electron 的 Chromium 加载实际生产构建，以本地模拟 API 验证：192 集且空字幕列表时入口可见；默认不选；选中后 POST 任务携带 `ai-zh`、`zh.*`，保留视频模式、账号、分集和合并设置；取消后移除预设，保留手动英文选择；其他网站及单视频原有选项不受影响。
- 临时界面检查脚本及截图位于 `/private/tmp/ytsage-subtitle-ui-check.cjs`、`/private/tmp/ytsage-subtitle-ui.png`，不进入仓库。
- 仅修改前端与文档，未运行后端测试、在线 B 站下载或 Docker 镜像构建；分集字幕参数继承已核对现有源码。
- `readme-translations/README.zh.md` 仅链接根 README，无需重复修改；界面中英文文案均已同步。
