---
title: "Compiler Error CS1648"
ms.custom: na
ms.date: 10/01/2016
ms.devlang: 
  - CSharp
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
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
# Compiler Error CS1648
Members of readonly field 'identifier' cannot be modified (except in a constructor or a variable initializer)  
  
 This error occurs when you attempt to modify a member of a field which is readonly where it is not allowed to be modified. To resolve this error, limit assignments to readonly fields to the constructor or variable initializer, or remove the readonly keyword from the declaration of the field.  
  
 The following sample generates CS1648:  
  
```  
// CS1648.cs  
public struct Inner  
  {  
    public int i;  
  }  
  
class Outer  
{    
  public readonly Inner inner = new Inner();  
}  
  
class D  
{  
   static void Main()  
   {  
      Outer outer = new Outer();  
      outer.inner.i = 1;  // CS1648  
   }  
}  
```