---
title: "Bien démarrer avec le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f5c2441148ba869629a88ab2fcc83131f5205493
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="get-started-with-the-net-framework"></a>Bien démarrer avec le .NET Framework
Le .NET Framework est un environnement d'exécution qui gère les applications ciblant le .NET Framework. Il se compose d'un Common Language Runtime, qui assure la gestion de la mémoire et d'autres services système, et d'une bibliothèque de classes étendue, qui permet aux programmeurs de tirer parti d'un code solide et fiable pour tous les domaines importants du développement d'applications.

<a name="Introducing"></a> 
## <a name="what-is-the-net-framework"></a>Qu'est-ce que le .NET Framework ?
 Le .NET Framework est un environnement d'exécution managé qui fournit divers services à ses applications actives. Il comporte deux composants principaux : le Common Langage Runtime (CLR), qui est le moteur d'exécution gérant les applications actives, et la bibliothèque de classes .NET Framework, qui fournit une bibliothèque de code testé réutilisable que les développeurs peuvent appeler à partir de leurs propres applications. Le .NET Framework fournit notamment les services suivants aux applications en cours d'exécution :

- Gestion de la mémoire Dans de nombreux langages de programmation, les programmeurs sont chargés d'allouer et de libérer la mémoire et de gérer les durées de vie des objets. Dans les applications .NET Framework, le CLR fournit ces services au nom de l'application.

- Système de type commun. Dans les langages de programmation traditionnels, les types de base sont définis par le compilateur, ce qui complique l'interopérabilité interlangage. Dans le .NET Framework, les types de base sont définis par le système de type .NET Framework et sont communs à tous les langages qui ciblent le .NET Framework.

- Bibliothèque de classes étendue. Afin d'éviter d'écrire des quantités importantes de code pour gérer les opérations de programmation de bas niveau courantes, les programmeurs peuvent utiliser une bibliothèque de types et de leurs membres facilement accessible à partir de la bibliothèque de classes .NET Framework.

- Infrastructures et technologies de développement. Le .NET Framework inclut des bibliothèques pour des domaines spécifiques de développement d'applications, tels qu'ASP.NET pour les applications web, ADO.NET pour l'accès aux données et Windows Communication Foundation pour les applications orientées service.

- Interopérabilité des langages. Les compilateurs de langage qui ciblent le .NET Framework émettent un code intermédiaire nommé Common Intermediate Language (CIL) qui est compilé à son tour au moment de l'exécution par le Common Language Runtime (CLR). Avec cette fonctionnalité, les routines écrites dans un langage sont accessibles à d'autres langages et les programmeurs peuvent se concentrer sur la création d'applications dans leur(s) langage(s) préféré(s).

- Compatibilité des versions. À de rares exceptions près, les applications qui sont développées à l'aide d'une version particulière du .NET Framework peuvent s'exécuter sans modification avec une version ultérieure.

- Exécution côte à côte. Le .NET Framework aide à résoudre les conflits de versions en permettant à plusieurs versions du Common Langage Runtime de cohabiter sur le même ordinateur. Cela signifie que plusieurs versions d'applications peuvent également coexister, et qu'une application peut s'exécuter sur la version du .NET Framework avec laquelle elle a été générée.

- Multi-ciblage. En ciblant la bibliothèque de classes portable .NET Framework, les développeurs peuvent créer des assemblys qui fonctionnent sur plusieurs plateformes .NET Framework, telles que Windows 7, Windows 8, Windows 8.1, Windows 10, Windows Phone et Xbox 360. Pour plus d’informations, consultez [Bibliothèque de classes portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

<a name="ForUsers"></a> 
## <a name="the-net-framework-for-users"></a>Le .NET Framework pour les utilisateurs
 Si vous ne développez pas d'applications .NET Framework, mais que vous les utilisez, vous n'êtes pas obligé d'avoir une connaissance précise du .NET Framework ou de son exécution. Pour la plus grande part, le .NET Framework est complètement transparent aux utilisateurs.

 Si vous utilisez le système d’exploitation Windows, le .NET Framework est peut-être déjà installé sur votre ordinateur. En outre, si vous installez une application qui requiert le .NET Framework, le programme d'installation de l'application peut installer une version spécifique du .NET Framework sur votre ordinateur. Dans certains cas, vous pouvez afficher une boîte de dialogue qui vous demande d'installer le .NET Framework. Si cette boîte de dialogue apparaît quand vous essayez d’exécuter une application et que votre ordinateur a accès à Internet, vous pouvez accéder à une page web qui vous permet d’installer la version manquante du .NET Framework.

 En règle générale, vous ne devez pas désinstaller les versions du .NET Framework installées sur votre ordinateur. Il existe deux raisons à cela :

- Si une application que vous utilisez dépend d'une version spécifique du .NET Framework, elle peut cesser de fonctionner si cette version est supprimée.

- Certaines versions du .NET Framework sont des mises à jour sur place de versions antérieures. Par exemple, le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] est une mise à jour sur place de la version 2.0, et le .NET Framework 4.6 est une mise à jour sur place des versions 4, 4.5, 4.5.1 et 4.5.2. Pour plus d’informations, consultez [Versions et dépendances du .NET Framework](../../../docs/framework/migration-guide/versions-and-dependencies.md).

 Si vous choisissez de supprimer le .NET Framework, désinstallez-le toujours à l’aide de l’option **Programmes et fonctionnalités** du Panneau de configuration. Ne supprimez jamais manuellement une version du .NET Framework.

 Notez que plusieurs versions du .NET Framework peuvent être chargées simultanément sur un même ordinateur. Cela signifie que vous n’avez pas besoin de désinstaller les versions antérieures afin d’installer une version ultérieure.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>Le .NET Framework pour les développeurs
 Si vous êtes développeur, vous pouvez choisir n'importe quel langage de programmation qui prenne en charge le .NET Framework pour créer votre application. Comme le .NET Framework fournit l'indépendance et l'interopérabilité des langages, vous pouvez interagir avec d'autres applications et composants .NET Framework, quel que soit le langage utilisé pour leur développement.

 Pour développer des applications ou des composants .NET Framework, procédez comme suit :

1. Si elle n’est pas préinstallée sur votre système d’exploitation, installez la version du .NET Framework ciblée par votre application. La dernière version en production est le .NET Framework 4.7, préinstallé sur Windows 10 Creative Update et disponible au téléchargement sur les versions précédentes du système d’exploitation Windows. Pour la configuration système requise du .NET Framework, consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md). Pour plus d’informations sur l’installation d’autres versions du .NET Framework, consultez [Guide d’installation](../../../docs/framework/install/guide-for-developers.md). Il existe des packages .NET Framework supplémentaires proposés hors bande. Pour plus d’informations sur ces packages, consultez [Versions finales hors plage du .NET Framework](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Sélectionnez le ou les langages .NET Framework à utiliser pour développer vos applications. Microsoft propose plusieurs langages, notamment Visual Basic, C#, Visual F# et C++. (Un langage de programmation qui vous permet de développer des applications pour le .NET Framework respecte la [spécification CLI (Common Language Infrastructure)](http://go.microsoft.com/fwlink/?LinkId=199862).)

3. Sélectionnez et installez l'environnement de développement que vous utiliserez pour créer vos applications et qui prend en charge le ou les langages de programmation sélectionnés. L’environnement de développement intégré de Microsoft pour les applications .NET Framework est [Visual Studio](http://go.microsoft.com/fwlink/?LinkId=325532). Il est disponible dans plusieurs versions commerciales ou gratuites.

 Pour plus d’informations sur le développement d’applications qui ciblent le .NET Framework, consultez [Guide de développement](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble](../../../docs/framework/get-started/overview.md)|Fournit des informations détaillées pour les développeurs qui génèrent les applications ciblant le .NET Framework.|
|[Guide d’installation](../../../docs/framework/install/index.md)|Fournit des informations sur l'installation du .NET Framework.|  
|[Versions finales hors plage de .NET Framework](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)|Décrit les versions finales hors plage du .NET Framework et leur utilisation dans votre application.|
|[Configuration système requise](../../../docs/framework/get-started/system-requirements.md)|Répertorie les configurations matérielle et logicielle requises pour exécuter le .NET Framework.|
|[.NET Core et Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md)|Décrit les nouveautés du .NET Core par rapport au .NET Framework, et comment accéder aux projets .NET Core open source.|
|[Documentation .NET Core](/dotnet/)|Documentation de référence sur les concepts et les API de .NET Core.|

## <a name="see-also"></a>Voir aussi
 [Guide du .NET Framework](../../../docs/framework/index.md)   
 [Nouveautés](../../../docs/framework/whats-new/index.md)   
 [Navigateur d’API .NET](/dotnet/api/)   
 [Guide de développement](../../../docs/framework/development-guide.md)

