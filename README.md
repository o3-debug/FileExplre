基于人工智能开发
基于 net10 和 WPF 的高性能文件管理器原型，针对高频目录切换和批量打开工作流进行了专门设计。

## 关键能力

- 异步高速目录枚举：使用 Win32 `FindFirstFileEx` 做后台扫描，避免主线程卡顿。
- 虚拟化文件列表：`DataGrid` 开启行/列虚拟化与回收模式，处理大目录更平稳。
- 收藏文件夹组：把一组常用目录保存下来，后续可一键全部打开为标签。
- 多标签工作流：同一窗口内并行管理多个目录，不需要频繁开新的资源管理器窗口。
- 即时筛选：对当前标签页结果做快速过滤。
- 系统互通：双击文件直接交给系统默认程序，支持复制路径、在系统资源管理器中打开。

## 项目结构

- `FileExplre.App`：WPF 主应用
- `Services/FastFileSystemService.cs`：高性能目录枚举实现
- `ViewModels/MainWindowViewModel.cs`：收藏组、标签管理、主操作编排
- `ViewModels/FolderTabViewModel.cs`：单个目录标签的导航、筛选与打开行为

## 运行方式

```powershell
dotnet build .\FileExplre.slnx
dotnet run --project .\FileExplre.App\FileExplre.App.csproj
```

## 收藏组存储

收藏组默认保存到：

`%LOCALAPPDATA%\OrbitFiles\favorites.json`
