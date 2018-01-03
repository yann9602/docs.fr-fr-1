---
title: "Assistant Débogage managé reportAvOnComRelease"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b198c6a026cded788c0030f1319b37e874d0eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reportavoncomrelease-mda"></a>Assistant Débogage managé reportAvOnComRelease
L'Assistant Débogage managé `reportAvOnComRelease` est activé quand des exceptions sont levées en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.  
  
## <a name="symptoms"></a>Symptômes  
 Violations d'accès et endommagement de la mémoire.  
  
## <a name="cause"></a>Cause  
 Parfois, une exception est levée en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts. Normalement, cette exception est ignorée, car elle entraînerait une violation d'accès dans le CLR et l'arrêt de ce dernier. Quand cet Assistant est activé, les exceptions de ce type peuvent être détectées et signalées au lieu d'être simplement ignorées.  
  
## <a name="resolution"></a>Solution  
 Examinez votre code de comptage de références, ainsi que les clients natifs de votre objet pour déterminer s'ils contiennent des erreurs de comptage.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Deux modes sont disponibles. Si l'attribut `allowAv` a pour valeur `true`, l'Assistant empêche le runtime d'ignorer la violation d'accès. Si l'attribut `allowAv` est défini sur `false` (valeur par défaut), le runtime ignore la violation d'accès, mais un message d'avertissement est présenté à l'utilisateur pour indiquer qu'une exception a été levée et ignorée.  
  
## <a name="output"></a>Sortie  
 Si possible, la sortie contient le vtable d'origine du pointeur d'interface COM. Sinon, un message d'information apparaît.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling d'interopérabilité](../../../docs/framework/interop/interop-marshaling.md)
