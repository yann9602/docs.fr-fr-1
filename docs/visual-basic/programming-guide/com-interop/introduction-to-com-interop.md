---
title: "Introduction à COM Interop (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 13df7dc6b325b97411b910c0fc8e05e65a332dc5
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="introduction-to-com-interop-visual-basic"></a>Introduction à COM Interop (Visual Basic)
Le modèle COM (Component Object) permet à un objet exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Alors que les objets COM ont été essentiels à la programmation de nombreuses années Windows, les applications conçues pour le common language runtime (CLR) offrent de nombreux avantages.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]applications va remplacer celles développées avec COM. Jusqu'à cette date, vous devrez peut-être utiliser ou créer des objets COM à l’aide de [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]. L’interopérabilité avec COM, ou *COM interop*, permet d’utiliser des objets COM existants lors de la transition vers le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] à votre propre rythme.  
  
 À l’aide de la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour créer des composants COM, vous pouvez utiliser COM interop sans inscription. Cela vous permet de contrôler quelle version de DLL est activée lorsque plusieurs versions sont installée sur un ordinateur et permet aux utilisateurs finaux d’utiliser XCOPY ou FTP pour copier votre application vers un répertoire approprié sur leur ordinateur où il peut être exécuté. Pour plus d’informations, consultez [COM Interop sans inscription](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Le Code managé et des données  
 Le code développé pour le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] est appelé *du code managé*et contient des métadonnées qui sont utilisée par le CLR. Données utilisées par [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] applications est appelée *les données gérées* , car le runtime gère les tâches liées aux données telles que l’allocation et de libération de la mémoire et d’exécuter la vérification de type. Par défaut, Visual Basic .NET utilise du code managé et les données, mais vous pouvez accéder à du code non managé et les données d’objets COM à l’aide des assemblys d’interopérabilité (décrites plus loin dans cette page).  
  
## <a name="assemblies"></a>Assemblys  
 Un assembly est le principal bloc de construction d’un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application. Il est un ensemble de fonctionnalités qui sont générées, créée et déployée comme une seule unité d’implémentation contenant un ou plusieurs fichiers. Chaque assembly contient un manifeste d’assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Bibliothèques de types et des manifestes d’Assembly  
 Bibliothèques de types décrivent les caractéristiques des objets COM, tels que les noms de membres et types de données. Manifestes d’assembly exécutent la même fonction pour [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] applications. Elles comprennent des informations sur les éléments suivants :  
  
-   Identité de l’assembly, version, culture et signature numérique.  
  
-   Fichiers qui composent l’implémentation de l’assembly.  
  
-   Types et ressources qui composent l’assembly. Comprennent celles qui sont exportés à partir de celui-ci.  
  
-   Dépendances de compilation des autres assemblys.  
  
-   Autorisations requises pour l’assembly pour s’exécuter correctement.  
  
 Pour plus d’informations sur les assemblys et les manifestes d’assembly, consultez [assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importation et exportation de bibliothèques de types  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]contient un utilitaire, Tlbimp, qui vous permet d’importer des informations à partir d’une bibliothèque de types dans un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application. Vous pouvez générer des bibliothèques de types provenant d’assemblys à l’aide de l’utilitaire Tlbexp.  
  
 Pour plus d’informations sur Tlbimp et Tlbexp, consultez [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) et [Tlbexp.exe (exportateur)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Assemblys d’interopérabilité  
 Assemblys PIA sont [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] le code d’assemblys qui pont entre managées et non managées, membres de l’objet COM mappage en équivalent [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] membres managés. Assemblys d’interopérabilité créés par Visual Basic .NET gèrent de nombreux détails de l’utilisation des objets COM, tels que le marshaling d’interopérabilité.  
  
## <a name="interoperability-marshaling"></a>Marshaling d’interopérabilité  
 Tous les [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] applications partagent un ensemble de types courants qui permettent l’interopérabilité des objets, quel que soit le langage de programmation qui est utilisé. Les paramètres et les valeurs de retour des objets COM utilisent parfois des types de données qui diffèrent de celles utilisées dans le code managé. *Marshaling d’interopérabilité* consiste à empaqueter des paramètres et valeurs de retour dans les types de données équivalents lors de leur déplacement vers et depuis des objets COM. Pour plus d’informations, consultez [Marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Voir aussi  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Procédure pas à pas : implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Interopération avec du code non managé](../../../../docs/framework/interop/index.md)  
 [Dépannage des problèmes liés à l’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (importateur de bibliothèques de types)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (exportateur de bibliothèques de types)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Marshaling d'interopérabilité](../../../framework/interop/interop-marshaling.md)  
 [COM Interop sans inscription](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
