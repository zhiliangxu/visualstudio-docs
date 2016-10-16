---
title: "Upgrading Project Items"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
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
# Upgrading Project Items
If you add or manage items inside project systems you do not implement, you may need to participate in the project upgrade process. Crystal Reports is an example of an item that can be added to the project system.  
  
 Typically, project item implementers want to leverage an already fully instantiated and upgraded project because they need to know what the project references are and what other project properties are there to make an upgrade decision.  
  
### To get the project upgrade notification  
  
1.  Set the <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading?qualifyHint=False> flag (defined in vsshell80.idl) in your project item implementation. This causes your project item VSPackage to auto load when the Visual Studio shell determines that a project system is in the process of upgrading.  
  
2.  Advise the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade?qualifyHint=False> interface via the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents?qualifyHint=False> method.  
  
3.  The <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade?qualifyHint=False> interface is fired after the project system implementation has completed its upgrade operations and the new upgraded project is created. Depending on the scenario, the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade?qualifyHint=False> interface is fired after the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution?qualifyHint=False>, the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject?qualifyHint=False>, or the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject?qualifyHint=False> methods.  
  
### To upgrade the project item files  
  
1.  You must carefully manage the file backup process in your project item implementation. This applies in particular for a side-by-side backup, where the `fUpgradeFlag` parameter of the <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject?qualifyHint=False> method is set to <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS?qualifyHint=False>, where files that had been backed up are placed along side files that are designated as ".old". The backed up files older than the system time when the project was upgraded can be designated as stale. Furthermore, they might be overwritten unless you take specific steps to prevent this.  
  
2.  At the time your project item gets a notification of the project upgrade, the **Visual Studio Conversion Wizard** is still displayed. Therefore, you should use the methods of the <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger?qualifyHint=False> interface to provide upgrade messages to the wizard UI.  
  
## See Also  
 [Visual Studio Conversion Wizard](assetId:///4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Upgrading Custom Projects](../VS_not_in_toc/Upgrading-Custom-Projects.md)