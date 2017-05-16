---
title: "Atténuation : cadres PNG dans les objets Icon | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9d5088d70397e21cb555c78b2701960ee69bde66
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-png-frames-in-icon-objects"></a>Atténuation : cadres PNG dans les objets Icon
À compter de .NET Framework 4.6 et versions ultérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> convertit correctement les icônes avec cadres PNG en objets <xref:System.Drawing.Bitmap>.  
  
 Dans les applications qui ciblent le .NET Framework 4.5.2 et versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet <xref:System.Drawing.Icon> comprend des cadres PNG.  
  
## <a name="impact"></a>Impact  
 Ce changement affecte les applications qui sont recompilées pour cibler le .NET Framework 4.6 et qui implémentent un traitement spécial pour <xref:System.ArgumentOutOfRangeException>, une exception levée quand un objet <xref:System.Drawing.Icon> comporte des cadres PNG. Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.  
  
### <a name="mitigation"></a>Atténuation  
 Si ce comportement est indésirable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la section [\<runtime](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :  
  
```  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
  
```  
  
 Si le fichier app.config contient déjà l’élément `AppContextSwitchOverrides` , la nouvelle valeur doit être fusionnée avec l’attribut `value` comme ceci :  
  
```  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
