---
title: "Comment : charger et décharger des assemblys (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 460d3a18fdee74c9b9c49ee465247b5b12d554d8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Comment : charger et décharger des assemblys (Visual Basic)
Les assemblys référencés par votre programme seront chargés automatiquement au moment de la génération, mais il est également possible de charger des assemblys spécifiques dans le domaine d’application actuel lors de l’exécution. Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).  
  
 Il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent. Même si l’assembly est hors de portée, le fichier d’assembly réel restera chargé jusqu'à ce que tous les domaines d’application qui le contiennent sont déchargées.  
  
 Si vous souhaitez décharger certains assemblys, mais pas d’autres, envisagez la création d’un nouveau domaine d’application, l’exécution du code à l’intérieur de ce domaine, puis déchargez le domaine. Pour plus d’informations, consultez [Comment : décharger un domaine d’Application](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Pour charger un assembly dans un domaine d’application  
  
1.  Utilisez une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain>et <xref:System.Reflection>.</xref:System.Reflection> </xref:System.AppDomain> Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).  
  
### <a name="to-unload-an-application-domain"></a>Pour décharger un domaine d’application  
  
1.  Il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent. Utilisez le `Unload` méthode <xref:System.AppDomain>pour décharger les domaines d’application.</xref:System.AppDomain> Pour plus d’informations, consultez [Comment : décharger un domaine d’Application](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
