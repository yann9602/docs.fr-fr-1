---
title: "Traçage réseau dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c8c915edee4fe23b1718f4820eff9998fa9e5836
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="network-tracing-in-the-net-framework"></a>Traçage réseau dans le .NET Framework
Le traçage réseau dans .NET Framework fournit l'accès aux informations sur les appels de méthodes et le trafic réseau généré par une application managée. Cette fonctionnalité permet de déboguer les applications en cours de développement et d'analyser celles qui sont déployées. La sortie fournie par un traçage réseau est personnalisable pour prendre en charge différents scénarios d'utilisation au moment du développement et dans un environnement de production.  
  
 Pour activer le traçage réseau dans .NET Framework, vous devez sélectionner une destination pour la sortie de traçage et ajouter des paramètres de configuration de traçage à l'application ou au fichier de configuration de l'ordinateur. Pour obtenir une description des fichiers de configuration et de leur mode d’utilisation, consultez [Fichiers de configuration](../../../docs/framework/configure-apps/index.md). Pour plus d’informations sur l’activation du traçage réseau, consultez [Activation du traçage réseau](../../../docs/framework/network-programming/enabling-network-tracing.md). Pour plus d’informations sur les paramètres que vous devez ajouter au fichier de configuration, consultez [Guide pratique pour configurer le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Lorsque la traçage est activé, vous pouvez capturer les informations de trace qui sont générées par les classes **System.Net**. Les membres de la classe réseau qui génèrent des informations de traçage contiennent la remarque suivante dans la section Remarques de la documentation bibliothèque de classes .NET Framework :  
  
> [!NOTE]
>  Ce membre génère des informations de traçage lorsque vous activez le traçage réseau dans votre application. Pour plus d'informations, consultez Traçage réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Activation du traçage réseau](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [Guide pratique pour configurer le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [Interprétation du traçage réseau](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [Introduction à l’instrumentation et au traçage](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)

