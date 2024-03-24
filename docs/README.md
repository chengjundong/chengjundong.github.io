# 20240324:PR view之提问
近期看得PR有点杂，来自不同的org。我发现一个特点，似乎中国同事不太提出comments，尤其是疑问形式的comments。  
一般来说，中国team的PR看着就很和谐，以approve为主。如果有comments，一般是命令形式。分为陈述，或以反问之形行命令之实
- 陈述："we need use XXX", "I think XXX is unnecessary"
- 以反问之形行命令之实: "why use XXX?", "why not XXX?"

从观点上来说，无论那种形式，都是指出对方这里写的不对。我认为，在reviewer充分理解PR作者的意图和实际需求的情况下，这样的comment也是可以接受的。  
同时，我想在此谈的是，有时候PR作者才是最了解需求的人，无论他了解得对不对。这也导致reviewer把重心放在code style，因为这是唯一他们可以发挥的地方。  
我认为可以在review中多尝试提问题，有以下几点思考
1. review不明白author的意图，可以提问让author回答这里的逻辑
2. author接收到这类问题，除了尝试回答以外，需要思考是不是自己的comments和unit test case不足以解释代码的逻辑
3. junior reviewer面对senior author可以通过提问，了解到为何对方会这样写代码，他的思考是什么，有什么可以学习到的
4. senior reviewer面对junior author可以通过提问，引导对方说出这样写的原因，如果确实有改进的地方则提供相关的建议。并不是senior一定知道的比junior多，在未完全了解作者意图和背后原因的情况下直接输出观点纠正，并不是非常的职业。

# 20240303:我反对用Github Copilot直接生成unit test
对于github copilot的使用已经有了一段时间了，于近期的分享会上听到这样的观点："As a sr.member, writting unit test is very boring, so you can use Copiloto help you..."  
听到这里我就把耳机摘了，我不认为这是sr member应有的态度，虽然他的unit test通过率可以达到95%以上，“效率”提升显著。  
这里有一个的谬误，对于我这样长期使用TDD的人来说，非常明显。copilot并不理解真正的business，如果只是根据implement来生成unit test，那么他会尽量生成一系列可以通过的unit test并且尽量包含所有可能的分支。这么做的前提是，implement是100%正确的，否则就是自掘坟墓。不过既然implement是100%正确，又为何需要unit test了？我想至少作者不需要，他的队友（回归测试需要）和领导（测试覆盖率指标）会需要。窃以为，该sr member平时的编程习惯里，并没有unit test这一项，就算写完implement之后也没有。导致他并不认为copilot生成一套“一定能通过的”测试有什么问题。  
仅仅以unit test效率来说，我认为，copilot应该帮助我们更快得写unit test，而不是直接对着业务代码生成全套unit test。