# OpenAI官方指南 [Prompt engineering](https://platform.openai.com/docs/guides/prompt-engineering/prompt-engineering)
>  本指南分享了从大型语言模型（有时称为GPT模型）如GPT-4中获取更好结果的策略和战术。这里描述的方法有时可以组合使用以获得更大的效果。我们鼓励尝试不同方法，找到适合您的最佳方法。
这里演示的一些示例目前仅适用于我们最强大的模型gpt-4。一般而言，如果发现一个模型在某个任务上失败，而有一个更强大的模型可用，通常值得尝试使用更强大的模型再次尝试。

六种提高效果的策略 [Six strategies for getting better results](https://platform.openai.com/docs/guides/prompt-engineering/six-strategies-for-getting-better-results)


## [Write clear instructions](https://platform.openai.com/docs/guides/prompt-engineering/write-clear-instructions) 写出清晰的指令
> **模型需要猜测的越少，你得到所需的可能性就越大。 具体、丰富、少歧义**
> 
> 这些模型无法读取你的思维。如果输出过长，请要求简短回复。如果输出过于简单，请要求专业水平的写作。如果你不喜欢格式，请展示你想看到的格式。



- [Include details in your query to get more relevant answers](https://platform.openai.com/docs/guides/prompt-engineering/tactic-include-details-in-your-query-to-get-more-relevant-answers)  **包含详细信息以获得更相关的答案**
  
> *为了获得高度相关的回复，请确保请求提供了任何重要的细节或上下文。否则你就把它留给模型去猜你的意思了。*

 ![image](./img/1-1include_details_prompt_demo.png)
  - 
- [Ask the model to adopt a persona](https://platform.openai.com/docs/guides/prompt-engineering/tactic-ask-the-model-to-adopt-a-persona) 要求模型扮演一个角色
  - 让系统扮演一个角色，他就会按照这个角色的思维思考
![image](./img/1-2persona.png)
- [Use delimiters to clearly indicate distinct parts of the input](https://platform.openai.com/docs/guides/prompt-engineering/tactic-use-delimiters-to-clearly-indicate-distinct-parts-of-the-input) 使用分隔符清楚地指示输入的不同部分
> 分隔符，如三引号、XML标记、章节标题等，可以帮助区分文本的不同部分。
>
> 对于像这样的简单任务，使用分隔符可能不会对输出质量产生影响。然而，任务越复杂，消除歧义的任务细节就变得更加重要。**不要让模型努力理解你究竟在问什么**。

- [Specify the steps required to complete a task](https://platform.openai.com/docs/guides/prompt-engineering/tactic-specify-the-steps-required-to-complete-a-task) 指定完成任务所需的步骤
  - 手把手教AI一步步怎么做，他就会跟着做
  - 
- [Provide examples](https://platform.openai.com/docs/guides/prompt-engineering/tactic-provide-examples) 提供示例模板
  - 提供适用于所有示例的一般指导通常比通过示例演示任务的所有排列组合更有效，但在某些情况下，提供示例可能更容易。例如，如果您希望模型模仿一种难以明确描述的用户查询响应风格。这被称为“few-shot”提示。
  - 
- [Specify the desired length of the output](https://platform.openai.com/docs/guides/prompt-engineering/tactic-specify-the-desired-length-of-the-output) 指定输出的期望长度
  - 你可以要求模型生成指定目标长度的输出。目标输出长度可以以词数、句子数、段落数、项目符号等形式指定。
  - 请注意，指示模型生成特定数量的单词在高精度上并不起作用。模型更可靠地生成具有特定段落数或项目符号数的输出。
  - 

## [Provide reference text](https://platform.openai.com/docs/guides/prompt-engineering/provide-reference-text) 提供参考文本 
> **AI幻觉 **语言模型可以自信地创造虚假答案，特别是在涉及深奥主题、引用和URL时。就像一张笔记纸可以帮助学生在考试中表现更好一样，向这些模型提供参考文本可以帮助它们以更少的捏造回答。


- [Instruct the model to answer using a reference text](https://platform.openai.com/docs/guides/prompt-engineering/tactic-instruct-the-model-to-answer-using-a-reference-text)  指示模型使用参考文本回答问题
  - 如果我们能为模型提供与当前查询相关的可信信息，那么我们可以指示模型使用提供的信息来构建其回答。
  - 一般用RAG来实现这个方案
  - 
- [Instruct the model to answer with citations from a reference text](https://platform.openai.com/docs/guides/prompt-engineering/tactic-instruct-the-model-to-answer-with-citations-from-a-reference-text) 指示模型从参考文本中引用答案
  - 如果输入已经得到相关知识的补充，可以直接要求模型通过引用提供的文档中的段落，在回答中添加引用。请注意，然后可以通过在提供的文档中进行字符串匹配来编程验证输出中的引用。
  - 

## [Split complex tasks into simpler subtasks](https://platform.openai.com/docs/guides/prompt-engineering/split-complex-tasks-into-simpler-subtasks) 将复杂的任务拆分为简单的子任务
> 正如在软件工程中将复杂系统分解为一组模块化组件是良好的实践一样，对于提交给语言模型的任务也是如此。复杂任务往往比简单任务具有更高的错误率。此外，复杂任务通常可以重新定义为一系列较简单任务的工作流程，在这些任务的输出被用于构建后续任务的输入。



- [Use intent classification to identify the most relevant instructions for a user query](https://platform.openai.com/docs/guides/prompt-engineering/tactic-use-intent-classification-to-identify-the-most-relevant-instructions-for-a-user-query) 使用意图分类来识别用户查询的最相关指令。  > 这个是针对开发的：
对于需要处理不同情况的大量独立指令集的任务，首先对查询类型进行分类并使用该分类确定所需的指令可能是有益的。这可以通过定义固定的类别并硬编码与处理给定类别任务相关的指令来实现。这个过程也可以递归应用，将任务分解成一系列阶段。这种方法的优势在于每个查询将仅包含执行任务下一阶段所需的指令，这可能导致较使用单个查询执行整个任务时更低的错误率。这也可能导致较低的成本，因为运行较大提示的成本更高

  - 
  - 
- [For dialogue applications that require very long conversations, summarize or filter previous dialogue](https://platform.openai.com/docs/guides/prompt-engineering/tactic-for-dialogue-applications-that-require-very-long-conversations-summarize-or-filter-previous-dialogue) 对于需要非常长对话的对话应用，总结或过滤先前的对话。
  - 由于有上下文的字数限制，所以对以前的对话打到一定长度后需要总结
    - 1、总结先前对话中的内容。      > 一旦输入达到预定的阈值长度，这可以触发一个查询，总结对话的一部分，先前对话的摘要可以作为系统消息的一部分包括。另外,先前的对话也可以在整个对话期间异步地进行总结
    - 2、动态选择先前对话中与当前查询最相关的部分 (查看使用外部工具[Use external tools 使用外部工具](https://workflowy.com/#/87f84b5d5b45) )
- [Summarize long documents piecewise and construct a full summary recursively](https://platform.openai.com/docs/guides/prompt-engineering/tactic-summarize-long-documents-piecewise-and-construct-a-full-summary-recursively) 逐段总结长文档，并递归构建完整摘要
  - 假设我们在总结一本书
    - 可以将各个部分的摘要连接在一起并进行总结，从而生成摘要的摘要。
    - 这个过程可以递归进行，直到整个文件被总结。
    - 如果需要使用关于较早部分的信息以理解较后部分，那么一个有用的技巧是在总结给定点处的内容时，包括在该点之前的文本的运行摘要。
    - 这个程序用于总结书籍的有效性已经在OpenAI的先前研究中使用GPT-3的变体进行了研究。

## [Give the model time to "think"](https://platform.openai.com/docs/guides/prompt-engineering/give-the-model-time-to-think) 给模型一些时间来 "思考"
> 思维链 如果被要求计算17乘以28，你可能不能立即知道，但仍然可以用时间来计算出来。同样，模型在试图立即回答问题时会产生更多的推理错误，而不是花时间来计算出答案。在回答之前要求“思考的过程”可以帮助模型更可靠地推理出正确答案。



- [Instruct the model to work out its own solution before rushing to a conclusion](https://platform.openai.com/docs/guides/prompt-engineering/tactic-instruct-the-model-to-work-out-its-own-solution-before-rushing-to-a-conclusion) 在匆忙得出结论之前，指示模型自己找出解决方案
  - 有时，当我们明确要求模型在得出结论之前从第一原理进行推理时，我们会获得更好的结果。例如，假设我们想让一个模型评估学生对数学问题的解决方案。最明显的方法是简单地询问模型学生的解决方案是否正确。
  -     > 这个是错误的示例

  -     > 这是好的示例

- [Use inner monologue or a sequence of queries to hide the model's reasoning process](https://platform.openai.com/docs/guides/prompt-engineering/tactic-use-inner-monologue-or-a-sequence-of-queries-to-hide-the-model-s-reasoning-process) 使用内心独白或一系列查询来隐藏模型的推理过程。  > 先前的策略表明，模型有时在回答特定问题之前详细思考问题是很重要的。对于一些应用程序，模型用于得出最终答案的推理过程可能不适合与用户共享。例如，在辅导应用程序中，我们可能希望鼓励学生自己解决问题，但模型对学生解决方案的推理过程可能会泄露答案给学生。
内心独白是一种可以用来缓解这个问题的策略。内心独白的想法是指示模型将那些应该对用户隐藏的输出部分放入一个结构化格式，使其易于解析。然后在呈现输出给用户之前，对输出进行解析并只使其中的一部分可见。
- [Ask the model if it missed anything on previous passes](https://platform.openai.com/docs/guides/prompt-engineering/tactic-ask-the-model-if-it-missed-anything-on-previous-passes)  询问模型在先前的处理中是否遗漏了任何内容
  - 模型容易把前面，尤其是中间的内容信息忽略，如果不重新检查， 模型就可能走偏，就像人聊天聊着聊到天南地北
  - 

## [Use external tools](https://platform.openai.com/docs/guides/prompt-engineering/use-external-tools) 使用外部工具
> 选择适合的（系统工具，LLM）
通过提供其他工具的输出来弥补模型的缺陷。例如，文本检索系统（有时称为RAG或检索增强生成）可以告诉模型相关文档的信息。像OpenAI的Code Interpreter这样的代码执行引擎可以帮助模型进行数学运算和代码运行。如果通过工具而不是语言模型可以更可靠或更高效地完成任务，请将其卸载以充分发挥双方的优势。



- [Use embeddings-based search to implement efficient knowledge retrieval](https://platform.openai.com/docs/guides/prompt-engineering/tactic-use-embeddings-based-search-to-implement-efficient-knowledge-retrieval) 使用基于嵌入的搜索实现高效的知识检索
- [Use code execution to perform more accurate calculations or call external APIs](https://platform.openai.com/docs/guides/prompt-engineering/tactic-use-code-execution-to-perform-more-accurate-calculations-or-call-external-apis) 使用代码执行来进行更准确的计算或调用外部 API。  > 语言模型不能单独准确执行算术或长时间的计算。在需要这样做的情况下，可以指示模型编写并运行代码，而不是进行自己的计算。特别是，可以指示模型将用于运行的代码放入指定的格式，例如三个反引号。生成输出后，可以提取并运行代码。最后，如果需要，可以将代码执行引擎（即Python解释器）的输出作为模型下一个查询的输入。
  - 
  - 方案二：调用外部API
  - 警告：执行模型生成的代码在本质上并不安全，因此在任何试图执行此操作的应用程序中都应采取预防措施。特别是需要一个沙盒式代码执行环境，以限制不受信任代码可能造成的危害。
  - 我：不要让AI直接执行代码，尽量让AI回调Function calling
- [Give the model access to specific functions](https://platform.openai.com/docs/guides/prompt-engineering/tactic-give-the-model-access-to-specific-functions) 赋予模型特定功能访问权限
  - 就是让AI告诉系统要执行某个方法，系统自己执行，Function calling
- 1 Backlink
  - 2、动态选择先前对话中与当前查询最相关的部分 (查看使用外部工具[Use external tools 使用外部工具](https://workflowy.com/#/87f84b5d5b45) )

## [Test changes systematically](https://platform.openai.com/docs/guides/prompt-engineering/test-changes-systematically) 系统地测试更改
> 提高性能更容易，如果你能够对其进行测量。在某些情况下，对提示进行修改可能会在一些孤立的例子上取得更好的性能，但导致在更具代表性的一组例子上性能更差。因此，要确保变更对性能的影响是净正的，可能需要定义一个全面的测试套件（也称为“评估”）。



有时很难确定一个变化，例如新的指令或新的设计，是否使您的系统变得更好还是更差。查看一些示例可能会暗示哪个更好，但是对于样本量较小的情况，很难区分真正的改进还是随机运气。也许这种变化有助于某些输入的性能，但对其他输入的性能有害。

- 评估程序（或“evals”）对于优化系统设计很有用。好的评估应该是：
  - 代表真实世界的使用情况（或至少多样化）
  - 包含许多测试用例以获得更强的统计力量（请参阅下表的指南）
  - 易于自动化或重复

[Tactic: Evaluate model outputs with reference to gold-standard answers](https://platform.openai.com/docs/guides/prompt-engineering/tactic-evaluate-model-outputs-with-reference-to-gold-standard-answers) 参照黄金标准答案评估模型输出

## [Other resources](https://platform.openai.com/docs/guides/prompt-engineering/other-resources)

-  [OpenAI Cookbook](https://cookbook.openai.com/),
- [Prompting libraries & tools](https://cookbook.openai.com/related_resources#prompting-libraries--tools)
- [Prompting guides](https://cookbook.openai.com/related_resources#prompting-guides)
- [Video courses](https://cookbook.openai.com/related_resources#video-courses)
- [Papers on advanced prompting to improve reasoning](https://cookbook.openai.com/related_resources#papers-on-advanced-prompting-to-improve-reasoning)

## 读后感：把AI当人

- **会犯错的才是AI，不会犯错的只是系统。**
- **人有人性，AI也有人性，一步步思考，回头检查等策略都很有用**
