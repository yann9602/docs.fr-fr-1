---
title: "Comment : enregistrer des assemblys PIA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40414f39a1b84e7d07086d0634898de5171db590
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-register-primary-interop-assemblies"></a>Comment : enregistrer des assemblys PIA
Les classes ne peuvent être marshalées que par COM Interop et sont toujours marshalées en tant qu’interfaces. Dans certains cas, l’interface utilisée pour marshaler la classe est appelée interface de classe. Pour plus d’informations sur la substitution de l’interface de classe par une interface de votre choix, consultez [Wrapper CCW (COM Callable Wrapper)](../../../docs/framework/interop/com-callable-wrapper.md).  
  
 Même s'il est possible d'utiliser des types COM à partir d'une application .NET Framework pour générer un assembly d'interopérabilité, une telle utilisation pose problème. Chaque fois qu'un développeur importe et signe une bibliothèque de types COM, il crée un ensemble de types uniques qui sont incompatibles avec ceux importés et signés par un autre développeur. La solution à ce problème d'incompatibilité de type est, pour chaque développeur, d'obtenir l'assembly PIA signé et fourni par le fournisseur.  
  
 Si vous envisagez d'exposer des types COM tiers à d'autres applications, utilisez toujours l'assembly PIA fourni par le même éditeur que la bibliothèque de types qu'il définit. En plus de garantir la compatibilité des types, les assemblys PIA sont souvent personnalisés par le fournisseur pour améliorer l'interopérabilité.  
  
 Même si vous ne souhaitez pas exposer des types COM tiers, l'utilisation d'un assembly PIA peut faciliter l'interopérabilité avec les composants COM. Toutefois, cette stratégie ne protège pas des modifications qu'un fournisseur peut apporter aux types définis dans un assembly PIA. Si votre application nécessite une telle protection, générez votre propre assembly d'interopérabilité au lieu d'utiliser un assembly PIA.  
  
 Vous devez inscrire tous les assemblys PIA acquis sur votre ordinateur de développement avant de pouvoir les référencer avec [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]. Visual Studio recherche et utilise un assembly PIA la première fois que vous référencez un type à partir d'une bibliothèque de types COM. Si Visual Studio ne peut pas localiser l'assembly PIA associé à la bibliothèque de types, il vous invite à l'acquérir ou vous propose de créer un assembly d'interopérabilité . De même, l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) utilise également le Registre pour rechercher des assemblys PIA.  
  
 Même s'il n'est pas nécessaire d'inscrire les assemblys PIA si vous ne prévoyez pas d'utiliser Visual Studio, l'inscription offre deux avantages :  
  
-   Un assembly PIA inscrit est clairement marqué sous la clé de Registre de la bibliothèque de types d'origine. L'inscription est le meilleur moyen de rechercher un assembly PIA sur votre ordinateur.  
  
-   Vous pouvez éviter de générer et d'utiliser par erreur un nouvel assembly d'interopérabilité si, à un moment donné, vous utilisez Visual Studio pour référencer un type pour lequel vous avez un assembly PIA non inscrit.  
  
 Utilisez l’outil [Regasm.exe (outil d’inscription d’assemblys)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) pour inscrire un assembly PIA.  
  
### <a name="to-register-a-primary-interop-assembly"></a>Pour inscrire un assembly PIA  
  
1.  À l'invite de commandes, tapez :  
  
     **regasm** *nomassembly*  
  
     Dans cette commande, *nomassembly* est le nom de fichier de l’assembly inscrit. Regasm.exe ajoute une entrée pour l'assembly PIA sous la même clé de Registre que la bibliothèque de types d'origine.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant inscrit l'assembly PIA `CompanyA.UtilLib.dll`.  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec des assemblys PIA](http://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e)  
 [Recherche d’assemblys PIA](http://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b)  
 [Redistribution d’assemblys PIA](http://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265)
