---
title: "Atténuation : cadres PNG dans les objets Icon"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2115f2cec327603373ebf566b4d6ccef6404c895
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="60708-102">Atténuation : cadres PNG dans les objets Icon</span><span class="sxs-lookup"><span data-stu-id="60708-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="60708-103">À compter du .NET Framework 4.6, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> convertit correctement les icônes dotées de cadres PNG en objets <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="60708-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="60708-104">Dans les applications qui ciblent le .NET Framework 4.5.2 et les versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="60708-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="60708-105">Impact</span><span class="sxs-lookup"><span data-stu-id="60708-105">Impact</span></span>  
 <span data-ttu-id="60708-106">Cette modification affecte les applications qui sont recompilées pour cibler le .NET Framework 4.6 et qui implémentent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée quand un objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="60708-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="60708-107">Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.</span><span class="sxs-lookup"><span data-stu-id="60708-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="60708-108">Atténuation</span><span class="sxs-lookup"><span data-stu-id="60708-108">Mitigation</span></span>  
 <span data-ttu-id="60708-109">Si ce comportement est indésirable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la section [\<runtime](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="60708-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="60708-110">Si le fichier app.config contient déjà l’élément `AppContextSwitchOverrides` , la nouvelle valeur doit être fusionnée avec l’attribut `value` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="60708-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="60708-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60708-111">See Also</span></span>  
 [<span data-ttu-id="60708-112">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="60708-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

