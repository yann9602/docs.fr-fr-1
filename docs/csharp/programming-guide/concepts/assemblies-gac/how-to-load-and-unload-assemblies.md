---
title: "Guide pratique pour charger et décharger des assemblys (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6bf6de24f4cbc3f3bd855b6d2cafa8120ebd90ee
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a>Guide pratique pour charger et décharger des assemblys (C#)
Les assemblys référencés par votre programme sont chargés automatiquement au moment de la génération, mais il est également possible de charger des assemblys spécifiques dans le domaine d’application actif au moment de l’exécution. Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent. Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés.  
  
 Si vous souhaitez décharger uniquement certains assemblys, créez un domaine d’application, exécutez le code à l’intérieur de ce domaine, puis déchargez le domaine. Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Pour charger un assembly dans un domaine d’application  
  
1.  Utilisez une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain> et <xref:System.Reflection>. Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Pour décharger un domaine d’application  
  
1.  Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent. Utilisez la méthode `Unload` de <xref:System.AppDomain> pour décharger les domaines d’application. Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [Guide pratique pour charger des assemblys dans un domaine d’application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

