# Visitor��Listener

ANTLR���������п���Ϊ���������������ṩ֧�֡�Ĭ������£�ANTLR����һ���﷨������Listener�ӿڣ������ж����˻ص�������������Ӧ���ڽ������������������¼���

��Listener��Visitor����֮�����Ĳ�ͬ�ǣ�Listener������ANTLR�ṩ�ı�����������ã���Visitor����������ʽ�ĵ���visit�����������ǵ��ӽڵ㣬��һ���ڵ���ӽڵ���������ǵ���visit��������ζ����Щ����û�еõ����ʡ�

���������ȴ�Listener��ʼ���������˽�Listener֮������Ҳ������ANTLR���������ѭVisitor���ģʽ������������

### �﷨������Listener

��Calc.java�����������д��룺

```
ParseTreeWalker walker = new ParseTreeWalker();
walker.walk(new DirectiveListener(), tree);
```

��ParseTreeWalker��ANTLR����ʱ�ṩ�����ڱ����﷨�������ʹ���Listener�лص�����������������ANTLR���߸���Calc.g�е��﷨�Զ�����ParseTreeListener�ӿڵ��ӽӿ�CalcListener��Ĭ��ʵ��CalcBaseListener�����к�������﷨��ÿ�������enter��exit������DirectiveListener�����Ǳ�д�ļ̳���CalcBaseListener�İ����ض�Ӧ�ô����ʵ�֣��������ݸ��������������������ڱ����﷨������ʱ�ͻᴥ��DirectiveListener�еĻص�������

![](http://codemany.com/uploads/calc-listener-hierachy.png)

��ͼ��ߵ��﷨��������ʾParseTreeWalkerִ����һ��������ȱ������ɴ����߱�ʾ����ͷ���������������ұ���ʾ�����﷨�������������������У�������ParseTreeWalker�������á�������������������assign�Ľڵ�ʱ��������enterAssign()���Ҹ�������AssignContext�﷨�������ڵ㡣����������������assign�ڵ�������ӽڵ��������exitAssign()��

![](http://codemany.com/uploads/listener-call-sequence.png)

Listener���Ƶ�ǿ��֮���������ж����Զ��ġ����ǲ���Ҫд�﷨���������������������ǵ�Listener����Ҳ����Ҫ��ʽ�ط������ǵ��ӽڵ㡣

### �﷨������Visitor

��Щ����£�����ʵ����Ҫ���Ƶ��Ǳ����������������ǿ�����ʽ�ص���visit����ȥ���������ڵ㡣ѡ��-visitor����ANTLR���ߴ���Ӧ�﷨����Visitor�ӿں�Ĭ��ʵ�֣����к�������﷨��ÿ�������visit������

��ͼ��������Ϥ��Visitorģʽ�������﷨�������ϡ���߲��ֵĴ����߱�ʾ�﷨��������������ȱ�������ͷ���������������ұ߲���ָ��Visitor�еķ����������С�

![](http://codemany.com/uploads/visitor-call-sequence.png)

������Calc.java�е����д��룺

```
EvalVisitor eval = new EvalVisitor();
// To start walking the parse tree
eval.visit(tree);
```

�������ȳ�ʼ�����Ƶ���������EvalVisitor��Ȼ�����visit()ȥ���������﷨��������ANTLR����ʱ�ṩ��Visitor֧�ִ�����ڿ������ڵ�ʱ����visitProg()�������visitProg()���������Ϊ��������visit����������������˵ȵȡ�

![](http://codemany.com/uploads/calc-visitor-hierachy.png)

ANTLR�Զ����ɵ�Visitor�ӿں�Ĭ��ʵ�ֿ���������ΪVisitor������д�Լ���ʵ�֣������Ǳ�����븲д�ӿ��е�ÿ�������������ǽ����۽������Ǹ���Ȥ�ķ����ϡ����ַ�������������ѧϰANTLR����Ҫ���ѵ�ʱ�䣬�����ǻص���������Ϥ�ı����������
