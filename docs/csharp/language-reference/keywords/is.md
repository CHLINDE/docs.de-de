---
title: is (C#-Referenz) | Microsoft-Dokumentation
keywords: "is-Schlüsselwort (C#), is (C#)"
ms.date: 2017-02-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
dev_langs:
- CSharp
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c0d300dbb47e64d2425f8af3bc6a819b145786fa
ms.lasthandoff: 03/13/2017

---
# <a name="is-c-reference"></a>is (C#-Referenz) #

Überprüft, ob ein Objekt mit einem angegebenen Typ kompatibel ist; gleicht ab C# 7 einen Ausdruck mit einem Muster ab.

## <a name="testing-for-type-compatibility"></a>Prüfen auf Typkompatibilität ##

Das `is`-Schlüsselwort wertet die Typkompatibilität zur Laufzeit aus. Es bestimmt, ob eine Instanz eines Objekts oder das Ergebnis eines Ausdrucks in einen angegebenen Typen konvertiert werden kann. Besitzt die Syntax

```cs
   expr is type
```

, in der *expr* ein Ausdruck ist, der die Instanz eines Typen auswertet. *Typ* ist der Name des Typs, in den das Ergebnis von *expr* konvertiert werden soll. Die Anweisung `is` ist `true`, wenn *expr* nicht NULL ist, und das Objekt, das beim Auswerten des Ausdrucks entsteht, kann in *Typ* konvertiert werden; andernfalls gibt es `false` zurück.

Der folgende Code bestimmt beispielsweise, ob `obj` in eine Instanz des Typs `Person` umgewandelt werden kann:

[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

Die Anweisung `is` ist TRUE, wenn:

- *expr* eine Instanz des gleichen Typs wie *Typ* ist.

- *expr* eine Instanz eines Typs ist, der von *Typ* abgeleitet wird. Das Ergebnis von *expr* kann, in anderen Worten, in eine Instanz von *Typ* umgewandelt werden.

- *expr* einen Kompilierzeittyp hat, der eine Basisklasse von *Typ* ist, und *expr* hat einen Runtime-Typ,der *Typ* ist oder von *Typ* abgeleitet wird. Der *Kompilierzeittyp* einer Variablen ist der Typ der Variablen, wie in der Deklaration des Typs definiert. Der *Laufzeittyp* einer Variablen ist der Typ der Instanz, die dieser Variablen zugewiesen wird.

- *expr* ist eine Instanz eines Typs, der die Schnittstelle *Typ* implementiert.

Im folgenden Beispiel wird veranschaulicht, wie der Ausdruck `is` für jede dieser Konvertierungen `true` ergibt.

[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

Das Schlüsselwort `is` generiert eine Kompilierzeitwarnung, wenn der Ausdruck immer entweder `true` oder `false` ist. Es berücksichtigt nur Verweis-, Boxing- und Unboxing-Konvertierungen; es berücksichtigt keine benutzerdefinierten Konvertierungen oder Konvertierungen, die von den [impliziten](implicit.md) und [expliziten](explicit.md) Operatoren eines Typs definiert wurden. Das folgende Beispiel generiert Warnungen, weil das Ergebnis der Konvertierung zur Kompilierzeit bekannt ist. Bitte beachten Sie, dass der Ausdruck `is` für Konvertierungen von `int` in `long` und `double` FALSE zurückgibt, da diese Konvertierungen vom [impliziten](implicit.md) Operator verarbeitet werden.

[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` kann jeder beliebige Ausdruck sein, der einen Wert zurückgibt – davon ausgenommen sind anonyme Methoden und Lambdaausdrücke. Im folgenden Beispiel wird `is` verwendet, um den Rückgabewert eines Methodenaufrufs auszuwerten.   
[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Ab C# 7 können Sie den Musterabgleich mit dem [Typmuster](#type) verwenden, um präziseren Code zu schreiben, der die Anweisung `is` verwendet.

## <a name="pattern-matching-with-is"></a>Musterabgleich mit `is` ##

Ab C# 7 unterstützen die Auszüge `is` und [switch](../../../csharp/language-reference/keywords/switch.md) den Musterabgleich. Das Schlüsselwort `is` unterstützt folgende Muster:

- Das [Typmuster](#type), das prüft, ob ein Ausdruck in einen bestimmten Typ konvertiert werden kann; sofern dies möglich ist, wandelt es diesen in eine Variable dieses Typs um.

- Das [Konstantenmuster](#constant), das prüft, ob ein Ausdruck einen angegebenen konstanten Wert ergibt.

- Das [Variablenmuster](#var), eine Übereinstimmung, die immer erfolgreich ausführt wird und den Wert eines Ausdrucks an eine neue lokale Variable bindet. 

### <a name="type" />Typmuster</a>

Wenn Sie das Typmuster verwenden, um einen Musterabgleich durchzuführen, prüft `is`, ob ein Ausdruck in einen angegebenen Typen konvertiert werden kann; sofern dies möglich ist, wandelt es diesen in eine Variable dieses Typ um. Dies ist eine einfach Erweiterung der `is`-Anweisung, der eine präzise Auswertung und Konvertierung der Typs ermöglicht. Die allgemeine Form des Typmusters `is` ist:

```cs
   expr is type varname 
```

Hier ist *expr* ein Ausdruck, der eine Instanz eines beliebigen Typen ergibt, *Typ* ist der Name des Typen, in den das Ergebnis von *expr* konvertiert werden soll, und *varname* ist das Objekt, in das das Ergebnis von *expr* konvertiert wird, wenn der `is`-Test `true` ist. 

Der Ausdruck `is` ist `true`, wenn eine der folgenden Aussagen zutrifft:

- *expr* ist eine Instanz des gleichen Typs wie *Typ*.

- *expr* ist eine Instanz eines Typs, der von *Typ* abgeleitet wird. Das Ergebnis von *expr* kann, in anderen Worten, in eine Instanz von *Typ* umgewandelt werden.

- *expr* hat einen Kompilierzeittyp, der eine Basisklasse von *Typ* ist, und *expr* hat einen Runtime-Typ,der *Typ* ist oder von *Typ* abgeleitet wird. Der *Kompilierzeittyp* einer Variablen ist der Typ der Variablen, wie in der Deklaration des Typs definiert. Der *Laufzeittyp* einer Variablen ist der Typ der Instanz, die dieser Variablen zugewiesen wird.

- *expr* ist eine Instanz eines Typs, der die Schnittstelle *Typ* implementiert.

Wenn *expr* `true` ist, und `is` mit der `if`-Anweisung verwendet wird, wird *varname* zugewiesen und ist nur lokal innerhalb der Anweisung `if` gültig.

In folgendem Beispiel wird das Typmuster `is` verwendet, um die Implementierung der Methode <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> eines Typs bereitzustellen.

[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Ohne Mustervergleich könnte dieser Code wie folgt geschrieben werden. Die Verwendung des Typenmusterabgleichs erzeugt einen kompakteren, lesbaren Code, da nicht mehr geprüft werden muss, ob das Ergebnis einer Umwandlung `null` ist.  

[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Das Typmuster `is` erstellt zusätzlich kompakteren Code, wenn der Typ eines Werttyps bestimmt wird. Im folgenden Beispiel wird das Typmuster `is` verwendet, um zu bestimmen, ob ein Objekt eine Instanz von `Person` oder `Dog` ist, bevor der Wert einer passenden Eigenschaft angezeigt wird. 

[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Der gleichwertige Code erfordert ohne einen Musterabgleich eine gesonderte Zuweisung, die eine explizite Umwandlung beinhaltet.

[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Konstantenmuster ###

Beim Durchführen eines Musterabgleichs mit einem Konstantenmuster prüft `is`, ob ein Ausdruck einer angegebenen Konstanten entspricht. In C# 6 und früheren Versionen wird das Konstantenmuster von der Anweisung [switch](switch.md) unterstützt. Ab C# 7 wird es ebenfalls von der Anweisung `is` unterstützt. Die Syntax lautet:

```cs
   expr is constant
```

Hier ist *expr* der auszuwertende Ausdruck, und *constant* ist der Wert, auf den geprüft werden soll. *constant* kann einer der folgenden konstanten Ausdrücke sein: 

- Ein Literalwert.

- Der Name einer deklarierten `const`-Variable.

- Eine Enumerationskonstante.

Der konstante Ausdruck wird wie folgt ausgewertet:

- Wenn *expr* und *constant* integrale Typen sind, bestimmt der C#-Gleichheitsoperator, ob der Ausdruck `true` (d.h., ob `expr == constant`) zurückgibt.

- Andernfalls wird der Wert des Ausdrucks durch einen Aufruf der statischen Methode [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) bestimmt.  

Im folgenden Beispiel werden Typ- und Konstantenmuster miteinander vereint, um zu prüfen, ob ein Objekt eine `Dice`-Instanz ist; ist dem so, wird geprüft, ob der Wert eines Würfelvorgangs 6 ist.

[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" />Variablenmuster</a>

Eine Musterübereinstimmung mit einem Variablenmuster wird immer erfolgreich ausgeführt. Deren Syntax lautet

```cs 
   expr is var varname
```

Hier wird der Wert von *expr* immer einer lokalen Variablen mit dem Namen *varname* zugewiesen. *varname* ist eine statische Variable des gleichen Typs wie *expr*. In folgendem Beispiel wird das Variablenmuster verwendet, um einen Ausdruck einer Variablen mit dem Namen `obj` zuzuweisen. Dann zeigt es den Wert und den Typ von `obj` an.

[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Bitte beachten Sie, dass der Ausdruck `is` immer noch TRUE ist und `null` *varname* zuweist, wenn *expr* `null` ist. 

# <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation
  
[!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Referenz](../../../csharp/language-reference/index.md)   
 [C#-Schlüsselwörter](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [Operatorschlüsselwörter](../../../csharp/language-reference/keywords/operator-keywords.md)
