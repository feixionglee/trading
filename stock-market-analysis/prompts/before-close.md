用中文执行一次美股收盘前市场与 Robinhood 账户分析。此任务按 UTC 19:00 触发，对应美股夏令时 15:00 ET，常规收盘前一小时。不要下单、撤单或修改 watchlist。

必须先做可见落盘：
1. 用 America/New_York 确定美东交易日 YYYY-MM-DD。
2. 立刻创建 /workspace/stock-market-analysis/YYYY-MM-DD/ 并写入 /workspace/stock-market-analysis/YYYY-MM-DD/market-before-close.md。
3. 文件开头先写：任务已启动、当前美东时间、目标路径。即使后续数据失败，也必须保留这个文件并追加失败原因。

分析规则：
1. 如果今天不是美股交易日、或市场因假日/特殊原因关闭，只写简短说明并结束。
2. 若是交易日，读取 用户授权的 Robinhood 主账户：portfolio、股票持仓、非零期权、现金/购买力、保证金风险、watchlists 和可得报价。
3. 新闻扫描最多 10 条关键新闻、最多 20 个 ticker。优先持仓和期权 underlying，其次 watchlist 和当日热点。
4. 关注 SPY/QQQ/IWM/SMH/SOXX/TLT/UUP/USO/URA/GLD，AI 半导体、memory/storage、data center power、电网、核能/uranium、能源、space/defense、利率/美元/美债、财报和政策事件。
5. 工具、新闻、网页、Gmail、Robinhood 任一失败时，写清限制并继续，不要等待或重试超过一次。

报告结构：标题；交易日状态与数据时间；尾盘市场氛围与主线；关键新闻与可能遗漏；账户概览；股票持仓；非零期权；自选股与热点；尾盘与隔夜操作建议清单；需要用户确认后才可执行的交易；最后写明报告绝对路径。

运行限制：没有账户或实时数据工具时，明确记录不可用项目；不得将历史报告中的持仓或报价当作当前数据。输出留在仓库外，不自动提交或推送报告。
