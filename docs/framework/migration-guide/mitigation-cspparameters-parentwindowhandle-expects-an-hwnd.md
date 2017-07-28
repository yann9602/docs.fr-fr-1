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
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a>Atténuation : CspParameters.ParentWindowHandle attend un HWND

La propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A>, introduite dans .NET Framework 2.0, permet à une application d’enregistrer une valeur de handle de fenêtre parente, pour que toute interface utilisateur nécessaire pour accéder à la clé (par exemple, une invite de code confidentiel ou de consentement) s’ouvre comme un enfant modal de la fenêtre spécifiée. À compter des applications qui ciblent .NET Framework 4.7, un handle de fenêtre (HWND) peut être affecté à cette propriété.

Dans les versions du .NET Framework jusqu’au .NET Framework 4.6.2, la valeur affectée à la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> devait être <xref:System.IntPtr> qui représentait l’emplacement de mémoire auquel se trouvait la valeur HWND. Sur Windows 7 et les versions antérieures du système d’exploitation Windows, la définition de la propriété sur `form.Handle` n’avait aucun effet, mais sur Windows 8 et versions ultérieures, cela déclenche un <xref:System.Security.Cryptography> avec le message « Le paramètre est incorrect. »

Depuis que les applications ciblent le .NET Framework 4.7, une application Windows Forms peut définir la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> avec du code, comme suit :

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a>Impact

Les applications ciblant .NET Framework 4.7 ou versions ultérieures qui souhaitent enregistrer une relation de fenêtre parente sont encouragées à utiliser la forme simplifiée :

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a>Atténuation

Les développeurs qui avaient identifié que la valeur correcte était l’adresse de l’emplacement de mémoire qui détenait la valeur `form.Handle` peuvent désactiver ce changement de comportement en définissant le commutateur <xref:System.AppContext> `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` avec la valeur `true` :

- En définissant des commutateurs de compatibilité par programmation dans l’instance <xref:System.AppContext>.

- En ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

À l’inverse, les utilisateurs qui souhaitent utiliser ce nouveau comportement pour les applications qui s’exécutent dans .NET Framework 4.7 mais ciblent une version antérieure peuvent définir le commutateur <xref:System.AppContext> avec la valeur `false`.
 
## <a name="see-also"></a>Voir aussi

[Reciblage des modifications dans le .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

