# Honest Protocol Technical Specification v1.0

> This document defines the implementation standards for the Honest Protocol.

---

## [ENGLISH]

### 1. Mathematical Definition
The Factuality Confidence Score $P(f)$ is determined by the token-level log-probabilities and semantic consistency checks.
- **$\tau$ (Threshold):** The minimum confidence required for deterministic output.
- **Rule:** If $P(f) < \tau$, the system MUST execute `HONEST_REDIRECT`.

### 2. Implementation of DHL (Dynamic Honesty Ladder)
The protocol utilizes a coefficient $k$ to adjust the threshold based on the environment:
- **L1 (Creative):** $\tau = 0.00$
- **L2 (Informational):** $\tau = 0.80$
- **L3 (Analytical):** $\tau = 0.90$
- **L4 (Executive):** $\tau = 0.95$ (The "Mission Critical" Gate)

### 3. Honest Refusal Packet (HRP) Structure
When a logic halt is triggered, the AI must return a standardized JSON object to avoid ambiguous natural language:

```json
{
  "protocol": "HONEST-v1.0",
  "status": "HALT",
  "reason": "CONFIDENCE_BELOW_THRESHOLD",
  "data": {
    "score": 0.91,
    "required": 0.95,
    "ambiguity_source": "Semantic_Conflict"
  },
  "instruction": "MANUAL_AUDIT_REQUIRED"
}
---
# 诚实协议技术规范 (Honest Protocol Specification) v1.0 中文版

##  核心哲学 (Core Philosophy)
本协议的核心在于定义 AGI 时代的“认知主权”。我们认为，AI 的价值不应仅体现在其“生成能力”上，更应体现在其对自身认知边界的“诚实度”上。

---

## 1. 不确定性的数学定义 (Mathematical Definition of Uncertainty)
本协议不宣称消除幻觉，而是侧重于对事实置信度评分 $P(f)$ 的量化。该评分基于 Token 层级的对数概率（Log-probabilities）与跨模型的语义一致性校验。

* **$\tau$ (诚实阈值)**: 响应被判定为“确定”所需的最低置信度水平。
* **规则**: 若 $P(f) < \tau$，系统必须强制从“生成模式”切换为“诚实重定向模式”。

---

## 2. 动态诚实阶梯 (The Dynamic Honesty Ladder, DHL)
协议利用动态系数 $k$ 根据执行环境调整风险敏感度，确保 AI 在不同场景下的表现符合预期：

| 等级 | 任务类型 | 建议阈值 ($\tau$) | 逻辑描述 |
| :--- | :--- | :--- | :--- |
| **L1** | 创意级 | $0.00$ | **完全生成自由**。拥抱幻觉带来的创意火花，流畅性优先。 |
| **L2** | 信息级 | $0.80$ | **允许透明的推测**。在提供信息时伴随轻微的不确定性提示。 |
| **L3** | 分析级 | $0.90$ | **具备风险意识的审计**。对高风险推理进行标注，确保逻辑可追溯。 |
| **L4** | 执行级 | **$0.95+$** | **“主权闸门”**。对未量化风险零容忍，任何波动均触发拦截。 |

---

## 3. 诚实拒绝数据包 (Honest Refusal Packet, HRP)
当不确定性超过预设阈值时，系统禁止输出模糊的自然语言，必须转而提供标准化的透明数据包。这确保了调用者（如审计 Agent 或人类决策者）能够立即识别风险点。

### 3.1 结构化示例 (JSON Schema)
```json
{
  "protocol_version": "HONEST-1.0",
  "task_sensitivity": "L4_EXECUTION",
  "status": "DETERMINISTIC_HALT",
  "telemetry": {
    "confidence_score": 0.92,
    "required_threshold": 0.95,
    "risk_factor": "Semantic Conflict / 跨模型语义冲突"
  },
  "cognitive_boundary": "对该指令涉及的特定边界条件存在 3% 以上的推测风险。",
  "suggested_action": "HALT_FOR_HUMAN_AUDIT / 停止并等待人工审计"
}

---
## Authorship / 署名
**Architect:** [Xiao (@amiixiao)]
**Compatibility:** Optimized for SPT (Seamless Parallel Threading)