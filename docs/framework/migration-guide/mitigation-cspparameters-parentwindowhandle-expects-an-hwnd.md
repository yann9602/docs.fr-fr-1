---
title: "Atténuation : CspParameters.ParentWindowHandle attend un HWND"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b65aaf7149ca29b2af3efdf44ee9489a04c73a2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a><span data-ttu-id="ebda6-102">Atténuation : CspParameters.ParentWindowHandle attend un HWND</span><span class="sxs-lookup"><span data-stu-id="ebda6-102">Mitigation: CspParameters.ParentWindowHandle Expects an HWND</span></span>

<span data-ttu-id="ebda6-103">La propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A>, introduite dans .NET Framework 2.0, permet à une application d’enregistrer une valeur de handle de fenêtre parente, pour que toute interface utilisateur nécessaire pour accéder à la clé (par exemple, une invite de code confidentiel ou de consentement) s’ouvre comme un enfant modal de la fenêtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ebda6-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property, introduced in the .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or a consent dialog) opens as a modal child to the specified window.</span></span> <span data-ttu-id="ebda6-104">À compter des applications qui ciblent .NET Framework 4.7, un handle de fenêtre (HWND) peut être affecté à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="ebda6-104">Starting with applications that target the .NET Framework 4.7, a window handle (HWND) can be assigned to this property.</span></span>

<span data-ttu-id="ebda6-105">Dans les versions du .NET Framework jusqu’au .NET Framework 4.6.2, la valeur affectée à la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> devait être <xref:System.IntPtr> qui représentait l’emplacement de mémoire auquel se trouvait la valeur HWND.</span><span class="sxs-lookup"><span data-stu-id="ebda6-105">In versions of the .NET Framework through the .NET Framework 4.6.2, the value assigned to the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property was expected to be an <xref:System.IntPtr> that represents the location in memory where the HWND value resided.</span></span> <span data-ttu-id="ebda6-106">Sur Windows 7 et les versions antérieures du système d’exploitation Windows, la définition de la propriété sur `form.Handle` n’avait aucun effet, mais sur Windows 8 et versions ultérieures, cela déclenche un <xref:System.Security.Cryptography> avec le message « Le paramètre est incorrect. »</span><span class="sxs-lookup"><span data-stu-id="ebda6-106">On Windows 7 and earlier versions of the Windows operating system, setting the property to `form.Handle` had no effect, but on Windows 8 and later versions, it results in a <xref:System.Security.Cryptography> with the message, "The parameter is incorrect."</span></span>

<span data-ttu-id="ebda6-107">Depuis que les applications ciblent le .NET Framework 4.7, une application Windows Forms peut définir la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> avec du code, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ebda6-107">Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a><span data-ttu-id="ebda6-108">Impact</span><span class="sxs-lookup"><span data-stu-id="ebda6-108">Impact</span></span>

<span data-ttu-id="ebda6-109">Les applications ciblant .NET Framework 4.7 ou versions ultérieures qui souhaitent enregistrer une relation de fenêtre parente sont encouragées à utiliser la forme simplifiée :</span><span class="sxs-lookup"><span data-stu-id="ebda6-109">Applications targeting the .NET Framework 4.7 or later that wish to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a><span data-ttu-id="ebda6-110">Atténuation</span><span class="sxs-lookup"><span data-stu-id="ebda6-110">Mitigation</span></span>

<span data-ttu-id="ebda6-111">Les développeurs qui avaient identifié que la valeur correcte était l’adresse de l’emplacement de mémoire qui détenait la valeur `form.Handle` peuvent désactiver ce changement de comportement en définissant le commutateur <xref:System.AppContext> `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` avec la valeur `true` :</span><span class="sxs-lookup"><span data-stu-id="ebda6-111">Developers who had identified that the correct value was the address of the memory location that held the `form.Handle` value can opt out of this change in behavior by setting the <xref:System.AppContext> switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="ebda6-112">En définissant des commutateurs de compatibilité par programmation dans l’instance <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="ebda6-112">By programmatically setting compatibility switches on the <xref:System.AppContext> instance.</span></span>

- <span data-ttu-id="ebda6-113">En ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="ebda6-113">By adding the following line to the `<runtime>` section of the app.config file:</span></span>
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

<span data-ttu-id="ebda6-114">À l’inverse, les utilisateurs qui souhaitent utiliser ce nouveau comportement pour les applications qui s’exécutent dans .NET Framework 4.7 mais ciblent une version antérieure peuvent définir le commutateur <xref:System.AppContext> avec la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ebda6-114">Conversely, users who wish to opt in to the new behavior for applications that run under the .NET Framework 4.7 but target an earlier version of the .NET Framework versions can set the <xref:System.AppContext> switch to `false`.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="ebda6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebda6-115">See also</span></span>

[<span data-ttu-id="ebda6-116">Reciblage des modifications dans le .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ebda6-116">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

