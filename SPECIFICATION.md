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
##[中文版]
###1. 数学定义
事实置信度评分 P(f) 由 Token 层级的对数概率 (log-probabilities) 与语义一致性校验共同决定。
• \tau (阈值): 确定性输出所需的最低置信度。
• 规则: 若 P(f) < \tau，系统必须执行“诚实重定向” (HONEST_REDIRECT)。
###2. 动态诚实阶梯 (DHL) 的实现
协议利用系数 k 根据环境调整阈值：
• L1 (创意级): \tau = 0.00
• L2 (信息级): \tau = 0.80
• L3 (分析级): \tau = 0.90
• L4 (执行级): \tau = 0.95
###3. 诚实拒绝数据包 (HRP) 结构
当逻辑停机被触发时，AI 必须返回标准化的 JSON 对象：
{
  "protocol": "HONEST-v1.0",
  "status": "HALT",
  "reason": "置信度低于阈值",
  "data": {
    "当前评分": 0.91,
    "要求阈值": 0.95,
    "模糊来源": "语义冲突"
  },
  "instruction": "需要人工审计"
}
---
## Authorship / 署名
**Architect:** [Xiao (@amiixiao)]
**Compatibility:** Optimized for SPT (Seamless Parallel Threading)