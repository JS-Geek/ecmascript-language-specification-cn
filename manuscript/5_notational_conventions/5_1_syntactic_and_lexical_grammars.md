# 5.1 Syntactic and lexical grammars

## 5.1.1 Context-Free Grammars
一个*上下文无关文法（context-free grammar）*由一组*产生式（productions）*组成。每个产生式有一个抽象符号称为*非终结符号（nonterminal）*作为它的*左部（left-hand side）*，以及包含零个或多个非终结符号和*终结符号（terminal）*的一个序列作为它的*右部（right-hand side）*。对于每个文法而言，终结符号都取自一个指定的符号表。  

一个*链式产生式*是一个有一个非终结符号和零个或多个终结符号在右部的产生式。  

从一个只包含一个独特的非终结符号（*目标符号，goal symbol*）的句子开始，一个给定的上下文无关文法定义了一种*语言（language）*，即终结符号序列的集合（甚至是无限的集合）。这些序列可以通过反复地把生成式序列中的非终结符号替换成以该非终结符号为左部的生成式的右部来生成。

## 5.1.2 The Lexical and RegExp Grammars
ECMAScript的*词法文法（lexical）*在规范[条款11](../11_ecmascript_language_lexical_grammar/README.md)中给出。该文法使用遵守[条款10.1](../10_scmascript_language_source_code/10_1_source_text.md)定义的*SourceCharacter*的Unicode编码点（code point）作为终结符号。该文法定义了一组产生式，起始于目标符号（goal symbol）*InputElementDiv*，*InputElementTemplateTail*，或*InputElementRegExp*，或*InputElementRegExpOrTemplateTail*，它们描述了代码点序列如何被转换成输入元素序列。  and

除空白符和注释外的输入元素，组成ECMAScript的句法（syntactic grammar）的终结符，被称为ECMAScrpit的记号（tokens）。这些记号是ECMAScript语言的保留字，标示符，字面量和标点符号。此外，断行符（line terminator）虽然不被认为是记号，但也是输入元素流（stream）的一部分，会引导自动分号插入（[automatic semicolon insertion](../11_ecmascript_language_lexical_grammar/11_9_automatic_semicolon_insertion.md)（[11.9](../11_ecmascript_language_lexical_grammar/11_9_automatic_semicolon_insertion.md)））的过程。简单的空白和单行注释会被删除，不会显示在句法的输入元素流中。一个*MultiLineComment*（即/\*...\*/形式的注释，无论它是否跨越了多行），如果没有包含断行符，同样会被删除，但如果包含了一个或多个断行符，则会被一个单独的断行符替换，成为句法的输入元素流的一部分。  

ECMAScript的*RegExp文法*在[21.2.1](../21_text_processing/21_2_regexp_objects.md)中定义。该文法有*SourceCharacter*定义的代码点作为自己的终结符号。它定义了一组产生式，起始于目标符号*Pattern*，它描述了代码点序列如何被转换成正则表达式模式。  

两个冒号“::”作为分隔符来区分词法和正则表达式文法的产生式。词法和正则表达式文法共享某些产生式。

## 5.1.3 The Numeric String Grammar

另一种文法用来把字符串转换成数字值。该文法类似于词法文法中和数字字面量有关的部分，它有自己的终结符号*SourceCharacter*。该文法在[7.1.3.1](../7_abstract_operations/7_1_type_conversion.md)中定义。  

三个冒号“:::”作为标点符号来区分数字字符串文法的产生式。

## 5.1.4 The Syntactic Grammar

ECMAScript的句法文法在条款11，12，13，14和15中定义。词法文法定义的ECMAScript记号作为该文法的终结符号。它定义了一组产生式，起始于两个可选的目标符号*Script*和*Module*，它们描述了记号序列如何组成句法正确的独立的ECMAScript程序组件。  

当一个代码点流被解析成ECMASCript脚本（*Script*）或模块（*Module*）时，它首先通过反复使用词法文法转换成输入元素流；然后这个输入元素流再使用一次句法文法进行解析。如果输入元素流中的记号符号无法被解析成目标非终结符（*Script*或*Module*）的一个单一实例且没有更多记号剩下时，输入流句法上存在错误。  

一个冒号“:”作为标点符号来区分句法文法的产生式。  

条款12，13，14和15中表示的句法文法并没有完整的说明一个正确的SCMAScript*脚本*或*模块*可以接受的记号序列。一些额外的特定记号序列也可以被接受，如在序列的某些特定位置（如在断行符前）插入分号也满足文法的描述。此外，文法描述的某些记号序列不被认为是文法可接受的，如一个断行字符出现在“尴尬”的位置。  

在某些情况下，为了避免模糊不清，句法文法使用泛化的产生式，这些产生式允许不能构成合法ECMAScript*脚本*或*模块*的记号序列。例如，该技术被用于对象字面量和对象解构模式。在这些情况下，提供了一个更严格的*补充文法*（*supplemental grammar*）来进一步限制可接受的记号序列。在特定的上下文中，当显示地指定时，输入元素对应的产生式会再次使用补充文法的目标符号进行解析。如果被一个表层文法（cover grammer）解析过的输入元素流中的记号符号无法被解析成对应的补充目标符号的一个单一实例且没有更多记号剩下时，输入流句法上存在错误。

## 5.1.5 Grammar Notation
词法的终结符，RegExp和数字字符串文法，包括文法的产生式和本规范中任何直接表示终结符的文字，都是用等宽字体显示。这些符号在脚本中出现时也和文本中一样显示。所有以这种方式指定的终结符代码点，都可以理解成相应的来自Basic Latin范围（range）的Unicode代码点，，而不是来自其他Unicode范围的任何看上去类似的代码点。  

