# 复现路线与代码入口

本文提供官方代码导航与补充材料清单。**本仓库没有训练实现，以下官方入口未在本次整理过程中执行。** 阅读这些路径不等于已经完成依赖安装或复现实验。

## 获取官方实现

[SPA-RL 官方仓库](https://github.com/WangHanLinHenry/SPA-RL-Agent) 由原作者维护。本文核对路径时参考的提交为 [`b1ccd776d990278fee5f42b2050bb35638f5ac1b`](https://github.com/WangHanLinHenry/SPA-RL-Agent/tree/b1ccd776d990278fee5f42b2050bb35638f5ac1b)。这只是代码导航的参考版本，**不是本项目历史实验所用版本的证明**。

如需继续研究，可在本档案目录之外单独获取官方实现：

```bash
git clone https://github.com/WangHanLinHenry/SPA-RL-Agent.git
cd SPA-RL-Agent
git checkout b1ccd776d990278fee5f42b2050bb35638f5ac1b
```

安装步骤、数据下载和环境区分以该提交的[官方说明](https://github.com/WangHanLinHenry/SPA-RL-Agent/blob/b1ccd776d990278fee5f42b2050bb35638f5ac1b/README.md)为准。该说明为环境评测和强化学习训练安排不同的依赖环境，运行前还需要调整模型与数据路径。

## 官方阶段入口

下表路径均相对于**官方实现目录**，不位于本仓库内。

| 阶段 | 官方路径 |
| --- | --- |
| 监督微调 | `sft/webshop_llama3b.sh` |
| 轨迹探索 | `exploration/webshop/my_generate_response_webshop.sh` |
| 进度训练数据整理 | `prm/data_org.py` |
| 进度评估器训练 | `prm/train_our_progress_model.py` |
| 逐步进度预测 | `prm/inference_prm.py` |
| 强化学习数据整理 | `prm/rl_data_org.py` |
| PPO 训练 | `ppo/train_ppo.sh` |
| 权重合并 | `ppo/merge.py` |
| WebShop 评测 | `eval/llama3_2_3b_eval_webshop.sh` |

## 继续复现的建议顺序

1. 固定官方版本，先记录环境、模型许可与计算资源。原论文使用 8 张各 48 GB 的 NVIDIA A6000；这是论文实验配置，不表示本机具备同等资源，也不表示所有实验都必须照搬该配置。
2. 明确数据来源和任务划分，先检查单个任务能否正常开始、执行动作并结束。
3. 检查监督微调输入格式和模型输出格式，再开展训练与基线评测。
4. 检查进度标签和奖励计算，再接入 PPO；记录相对上游的每一项修改。
5. 用相同测试任务与标准指标比较两个模型，保存可重新统计的逐任务记录。

上面的顺序是后续工作建议，不是本项目已执行步骤的证明。需要补充的证据详见[实验记录与核验](EXPERIMENTS.md)。

## 当前整理范围

本次工作仅整理文档与代码入口，没有迁入官方代码、修改算法、下载训练数据或模型，也没有重新训练。后续加入实现时，应同时保留上游作者与许可证信息，并更新本仓库当前的文档文件白名单规则。
