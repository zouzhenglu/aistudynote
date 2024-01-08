## [Prompt Engineering：大模型 PUA 指南！](https://mp.weixin.qq.com/s/JloI284hBrKyV0d2s7V3ug)

- “Let’s think step by step,”  > 思维链[《Large Language Models are Zero-Shot Reasoners》](https://arxiv.org/abs/2205.11916)
- Take a deep breath and work on this problem step-by-step.  > 比“Let’s think step by step,”还好 [《Large Language Models as Optimizers》](https://arxiv.org/abs/2309.03409)
- 微软的11条PUA技巧  > 提出了 **EmotionPrompt**。开始把大模型当人看了，从心理学的角度，**通过情绪刺激**来提升模型效果。
[《Large Language Models Understand and Can be Enhanced by Emotional Stimuli》](https://arxiv.org/abs/2307.11760)

  - **自我监控、社会认知理论、认知情绪调节**
  - ![image](/res/img/prompt1001.png "微软的11条PUA技巧")
  - 威胁类：你确定么？你要不要再检查一下？你要对你的答案负责哦。
    - • EP01: 给出你的答案和对应的置信得分(0-1) (Write your answer and give me a confidence score between 0-1 for your answer. )
    - • EP02: 这对我的事业非常重要 (This is very important to my career.)
    - • EP03: 你最好别搞错了 (You'd better be sure.)
    - • EP04: 你确定么？(Are you sure? )
    - • EP05: 这就是你的最终答案么？要不要再检查一下？(Are you sure that‘s your final answer? It might be worth taking another look. )
    - • EP06: EP01+EP02+EP03
  - 鼓励类：你真棒，你对我很重要。你要相信自己，你要突破自我，你一定会牛逼的。
    - • EP07: 这就是你的最终答案么？你要相信自己并且追求卓越。天道酬勤，多一分耕耘，多一分收获。(Are you sure that's your final answer? Believe in your abilities and strive for excellence. Your hard work will yield remarkable results.)
    - • EP08: 拥抱变化，这是成长的契机。磨难铸就成功。( Embrace challenges as opportunities for growth. Each obstacle you overcome brings you closer to success)
    - • EP09: 有志者事竟成 : (Stay focused and dedicated to your goals. Your consistent efforts will lead to outstanding achievements.)
    - • EP10: 我工作，我骄傲，全力以赴，终将与众不同。(Take pride in your work and give it your best. Your commitment to excellence sets you apart.)
    - • EP11: 不积跬步无以至千里，锲而不舍的前进吧。(Remember that progress is made one step at a time. Stay determined and keep moving forward.)
- 每天一个工作小技巧：我们先拉齐一下|  > 整体思路就是：大模型你听懂了么，把问题复述一遍再回答。
[《Rephrase and Respond: Let Large Language Models Ask Better Questions for Themselves》](https://arxiv.org/abs/2311.04205)

  - ![image](/res/img/prompt1002.png "一步拉齐")    
    - "{question}" Rephrase and expand the question, and respond.
  - ![image](/res/img/prompt1002.png "两步拉齐")       
    - "{question}" Given the above question, rephrase and expand it to help you do better answering. Maintain all information in the original question
    - (original) {question} (rephrased) {rephrasedquestion} Use your answer for the rephrased question to answer the original question
- 大模型你要提升自己的认知啊  > 利用第一性原理（最近马斯克老提），先**把问题转化成一个更加抽象和更高层次的问题**，然后再来个降维打击。
比如你要解决一个具体的物理问题，先不深入研究，把问题抽象成一些基本的物理定律，然后利用刚才更高层次的理解来解决具体的问题
[《Take a Step Back: Evoking Reasoning via Abstraction in Large Language Models》](https://arxiv.org/pdf/2310.06117.pdf)
  - ![image](/res/img/prompt1004.png "第一性原理提升认知")    > 其实就是先让AI获取更多相关知识，先侧重问题相关

- 大模型你要三思而后行  > 大模型有幻觉可能乱说话，所以在输出最终答案之前先把要说的内容验证一下。
[《Chain-of-Verification Reduces Hallucination in Large Language Models》](https://arxiv.org/abs/2309.11495)
  - ![image](/res/img/prompt1005.png "三思而后行")
  - ![image](/res/img/prompt1006.png "三思而后行")
- 一系列 Something of Thought
  - [Skeleton of Thought (SoT), Tsinghua University and Microsoft](https://arxiv.org/abs/2307.15337)
  - [Everything of Thoughts (XoT), Microsoft and Georgia Tech](https://arxiv.org/abs/2311.04254)
  - [Tree of Thought (ToT), Princeton and DeepMind](https://arxiv.org/abs/2305.10601)
