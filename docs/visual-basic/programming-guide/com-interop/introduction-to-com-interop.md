---
title: "Introduction à COM Interop (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8866dbadca040c57ed2b59540dd2c341eb81758c
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a>Introduction à COM Interop (Visual Basic)
Le modèle COM (Component Object) permet un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Bien que les objets COM ont été essentiels à de nombreuses années de programmation Windows, les applications conçues pour le common language runtime (CLR) offrent de nombreux avantages.  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]applications va remplacer celles développées avec COM. Jusqu'à cette date, vous devrez peut-être utiliser ou créer des objets COM à l’aide de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. L’interopérabilité avec COM, ou *COM interop*, vous permet d’utiliser des objets COM existants lors de la transition vers le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] à votre propre rythme.  
  
 À l’aide de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] pour créer des composants COM, vous pouvez utiliser COM interop sans inscription. Cela vous permet de contrôler quelle version de DLL est activée lorsque plusieurs versions sont installée sur un ordinateur et permet aux utilisateurs finals d’utiliser XCOPY ou FTP pour copier votre application vers un répertoire approprié sur leur ordinateur où elle peut être exécutée. Pour plus d’informations, consultez [Registration-Free COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Le Code managé et des données  
 Le code développé pour le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] est appelé *du code managé*et contient des métadonnées utilisées par le CLR. Données utilisées par [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications est appelée *données managées* , car le runtime gère les tâches liées aux données telles que la vérification de type allocation et libération de la mémoire et d’exécution. Par défaut, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] utilise le code géré et données, mais vous pouvez accéder à du code non managé et les données d’objets COM à l’aide des assemblys d’interopérabilité (décrits plus loin sur cette page).  
  
## <a name="assemblies"></a>Assemblys  
 Un assembly est le bloc de construction principal d’une [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application. Il est un ensemble de fonctionnalités qui sont générées, version et déployées comme une seule unité d’implémentation contenant un ou plusieurs fichiers. Chaque assembly contient un manifeste d’assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Bibliothèques de types et manifestes d’Assembly  
 Bibliothèques de types décrivent les caractéristiques des objets COM, tels que les noms des membres et types de données. Manifestes d’assembly exécutent la même fonction pour [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] les applications. Elles comprennent les informations suivantes :  
  
-   Identité de l’assembly, version, culture et signature numérique.  
  
-   Fichiers constituant l’implémentation de l’assembly.  
  
-   Types et ressources qui composent l’assembly. Comprennent celles qui sont exportés à partir de celui-ci.  
  
-   Dépendances de compilation des autres assemblys.  
  
-   Autorisations requises pour l’assembly fonctionne correctement.  
  
 Pour plus d’informations sur les assemblys et les manifestes d’assembly, consultez [assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importation et exportation de bibliothèques de types  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]contient un utilitaire, Tlbimp, qui vous permet d’importer des informations à partir d’une bibliothèque de types dans un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application. Vous pouvez générer des bibliothèques de types provenant d’assemblys à l’aide de l’utilitaire Tlbexp.  
  
 Pour plus d’informations sur Tlbimp et Tlbexp, consultez [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) et [Tlbexp.exe (exportateur de bibliothèques)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Assemblys d’interopérabilité  
 Les assemblys PIA sont [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] les assemblys qui pont entre managé et code, membres de l’objet COM mappage équivalent [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] membres managés. Assemblys d’interopérabilité créés par [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] gèrent de nombreux détails de l’utilisation des objets COM, tels que le marshaling d’interopérabilité.  
  
## <a name="interoperability-marshaling"></a>Marshaling d’interopérabilité  
 Tous les [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications partagent un ensemble de types courants qui permettent l’interopérabilité des objets, quel que soit le langage de programmation qui est utilisé. Les paramètres et les valeurs de retour des objets COM utilisent parfois des types de données qui diffèrent de ceux utilisés dans du code managé. *Marshaling d’interopérabilité* est le processus empaqueter des paramètres et valeurs de retour dans des types de données équivalents lors de leurs déplacements vers et depuis des objets COM. Pour plus d’informations, consultez [Marshaling d’interopérabilité](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="see-also"></a>Voir aussi  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Interopération avec du Code non managé](https://msdn.microsoft.com/library/sd10k43k)   
 [Résolution des problèmes d’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (exportateur de bibliothèques)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [Marshaling d’interopérabilité](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [COM Interop sans inscription](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
