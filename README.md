# EvidenceCourt v1 · Independent contract kit / 独立合约资料包

## 中文

这是可脱离 Greybox 游戏界面使用的证据裁决引擎。主文件为 `contracts/EvidenceCourt.py`；五关案卷位于 `public/campaign/manifests.json`；不依赖游戏的新案卷示例位于 `examples/standalone-case.json`。

**Studionet 已完成共享合约部署与五份案卷验证；五关共 10 次玩家签名对局全部 FINALIZED / SUCCESS，6 次成立、4 次不成立。** [合约](https://explorer-studio.genlayer.com/address/0x4CB540105c519Ce23912e2Edad5f4c34f25A9D2A) · [部署交易](https://explorer-studio.genlayer.com/tx/0x4f60c1832bf82a84be02dd78bcd4726d421cd49cfada9b07421218f41ad65208) · [逐局交易凭据](docs/verification.md)。

最快演示：在支持该 GenLayer Python 依赖的开发环境部署主合约，构造参数传入 `examples/standalone-case.json` 的完整内容作为一个字符串。查询 `get_engine()` 获取发布者，再读取 `get_catalog(发布者)`。使用返回的案件键提交以下选择，图像列表为空：

```json
{"evidence":["door-log","desk-log"],"tactic":"corroborate","target":"open","focus":"","sequence":[],"allocation":{},"argument":""}
```

模型正确提取事实时，两份独立记录支持成立；将 `desk-log` 换成 `old-poster` 则缺少证明。每局使用新的 32 位小写十六进制局号。真实结果需经过网络共识与最终确认。

本地运行：Python 3.12+，安装 `requirements-contract-tests.txt`，在资料包根目录运行 `python -m pytest -q tests/test_evidence_court.py`。测试替代模型和网页，验证合约逻辑，不冒充真实网络结果。旧 GenVM 下载地址的恢复方法见 `docs/evidence-court-guide.md`。

完整双语接口、扩展方式、发布共享地址和信任边界都在指南中。五关案卷的网页地址指向游戏站点；自行托管时必须改为你控制的稳定地址，核对字节哈希，再注册新案件版本。`SHA256SUMS.txt` 用于核对资料包内容。

## English

This engine works independently of the Greybox game interface. Deploy `contracts/EvidenceCourt.py` with a JSON-array string as its constructor argument. The complete campaign manifests are in `public/campaign/manifests.json`; `examples/standalone-case.json` provides a separate minimal demonstration.

**The shared engine and five cases are deployed on Studionet. Ten signed rounds across all five cases are FINALIZED / SUCCESS: six PROVED and four NOT_PROVED.** [Contract](https://explorer-studio.genlayer.com/address/0x4CB540105c519Ce23912e2Edad5f4c34f25A9D2A) · [Deployment](https://explorer-studio.genlayer.com/tx/0x4f60c1832bf82a84be02dd78bcd4726d421cd49cfada9b07421218f41ad65208) · [Round receipts](docs/verification.md).

For the smallest demonstration, pass the standalone case file's complete contents as one string when deploying. Read `get_engine()` and `get_catalog(publisher)` to obtain its case key. Submit the selection above with an empty image list and a new 32-character lowercase hexadecimal round ID. With correct fact extraction, the two independent records prove the claim; replacing `desk-log` with `old-poster` does not. Real outcomes still require network consensus and successful finalization.

For local tests, use Python 3.12+, install `requirements-contract-tests.txt`, and run `python -m pytest -q tests/test_evidence_court.py` from the kit root. Models and web responses are mocked. See the guide for the old GenVM archive recovery procedure.

`docs/evidence-court-guide.md` contains the full bilingual API, extension/deployment procedure and trust limits. Campaign web evidence points to the game site; self-hosted copies must use stable URLs you control with matching byte hashes and a newly registered version. `SHA256SUMS.txt` records package-file hashes.
