---
title: "&#39;ReDim&#39; cannot change the number of dimensions of an array"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
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
# &#39;ReDim&#39; cannot change the number of dimensions of an array
You have attempted to use `ReDim` to change the rank (number of dimensions) of an array. The `ReDim` statement can be used to change the size of one or more dimensions of an array that has already been formally declared, but it cannot change the rank of an array.  
  
 **Error ID:** BC30415  
  
### To correct this error  
  
-   Make sure that you intend the rank instead of the sizes of the array, and if possible, use `Dim` to declare a new array with the desired rank.  
  
## See Also  
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD Overview of Arrays in Visual Basic](assetId:///ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)