---
title: "Option Strict On does not allow narrowing in implicit type conversions between the lambda expression and delegate &#39;&lt;delegatename&gt;&#39;"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
manager: douge
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# Option Strict On does not allow narrowing in implicit type conversions between the lambda expression and delegate &#39;&lt;delegatename&gt;&#39;
With `Option Strict` on, you cannot have a narrowing conversion between the data type of a parameter in a delegate and the corresponding parameter of a lambda expression assigned to a variable of that delegate type. For example, in the following code, delegate `Del` has one parameter of type `Integer`.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 Therefore, the corresponding parameter of any lambda expression assigned to a variable of type `Del` can be an `Integer` or any data type for which there is a widening conversion from `Integer`.  
  
```vb#  
' Valid.  
Dim example1 As Del = Function(n As Integer) "Valid"  
Dim example2 As Del = Function(n As Long) "Valid"  
  
' Not valid.  
Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **Error ID:** BC36662  
  
### To correct this error  
  
-   Change the data type of the parameter in the delegate or the lambda expression so that the required widening relationship exists.  
  
-   Do not specify parameter data types in the lambda expression. Types will be inferred from the corresponding parameters in the delegate.  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## See Also  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)