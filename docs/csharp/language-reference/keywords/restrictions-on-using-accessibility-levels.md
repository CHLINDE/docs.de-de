---
title: Einschränkungen bei der Verwendung von Zugriffsebenen (C#-Referenz)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172408"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Einschränkungen bei der Verwendung von Zugriffsebenen (C#-Referenz)
Wenn Sie in einer Deklaration einen Typ angeben, überprüfen Sie, ob die Zugriffsebene dieses Typs von der Zugriffsebene eines Members oder eines anderen Typs abhängt. Auf die direkte Basisklasse muss z.B. mindestens genauso zugegriffen werden können wie auf die abgeleitete Klasse. Die folgende Deklaration verursacht einen Compilerfehler, da die Basisklasse `BaseClass` eine stärkere Zugriffsbeschränkung hat als `MyClass`:  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 In der folgenden Tabelle werden die Einschränkungen für deklarierte Zugriffsebenen zusammengefasst.  
  
|Kontext|Hinweise|  
|-------------|-------------|  
|[Klassen](../../../csharp/programming-guide/classes-and-structs/classes.md)|Die direkte Basisklasse eines Klassentyps muss mindesten dieselben Zugriffsmöglichkeiten wie der Klassentyp selbst bieten.|  
|[Schnittstellen](../../../csharp/programming-guide/interfaces/index.md)|Die explizite Basisschnittstelle eines Schnittstellentyps muss mindesten dieselben Zugriffsmöglichkeiten bieten wie der Schnittstellentyp selbst.|  
|[Delegaten](../../../csharp/programming-guide/delegates/index.md)|Die Rückgabe- und Parametertypen eines Delegattyps müssen mindestens dieselben Zugriffsmöglichkeiten wie der Delegattyp selbst bieten.|  
|[Konstanten](../../../csharp/programming-guide/classes-and-structs/constants.md)|Der Typ einer Konstante muss mindestens dieselben Zugriffsmöglichkeiten wie die Konstante selbst bieten.|  
|[Felder](../../../csharp/programming-guide/classes-and-structs/fields.md)|Der Typ eines Felds muss mindestens dieselben Zugriffsmöglichkeiten bieten wie das Feld selbst.|  
|[Methoden](../../../csharp/programming-guide/classes-and-structs/methods.md)|Die Rückgabe- und Parametertypen einer Methode müssen mindestens dieselben Zugriffsmöglichkeiten bieten wie die Methode selbst.|  
|[Eigenschaften](../../../csharp/programming-guide/classes-and-structs/properties.md)|Der Typ einer Eigenschaft muss mindestens dieselben Zugriffsmöglichkeiten bieten wie die Eigenschaft selbst.|  
|[Ereignisse](../../../csharp/programming-guide/events/index.md)|Der Typ eines Ereignisses muss mindestens dieselben Zugriffsmöglichkeiten bieten wie das Ereignis selbst.|  
|[Indexer](../../../csharp/programming-guide/indexers/index.md)|Der Typ und die Parametertypen eines Indexers müssen mindestens dieselben Zugriffsmöglichkeiten bieten wie der Indexer selbst.|  
|[Operatoren](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Die Rückgabe- und Parametertypen eines Operators müssen mindestens dieselben Zugriffsmöglichkeiten bieten wie der Operator selbst.|  
|[Konstruktoren](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Die Parametertypen eines Konstruktors müssen mindestens dieselben Zugriffsmöglichkeiten bieten wie der Konstruktor selbst.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält fehlerhafte Deklarationen verschiedener Typen. Der Kommentar nach jeder Deklaration gibt den erwarteten Compilerfehler an.  
  
```csharp  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a>C#-Programmiersprachenspezifikation  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Referenz](../../../csharp/language-reference/index.md)  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [C#-Schlüsselwörter](../../../csharp/language-reference/keywords/index.md)  
 [Zugriffsmodifizierer](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Zugriffsdomäne](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Zugriffsebenen](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Zugriffsmodifizierer](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
