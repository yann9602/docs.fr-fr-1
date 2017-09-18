---
title: Compilation d'applications avec .NET Native
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
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 76645ae43ce6754ffdf505729ec1198785a71561
ms.contentlocale: fr-fr
ms.lasthandoff: 09/18/2017

---
# <a name="compiling-apps-with-net-native"></a>Compilation d'applications avec .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] est une technologie de précompilation fournie avec [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]qui permet de générer et de déployer des applications Windows. Elle compile automatiquement la version commerciale des applications écrites en code managé (C# ou Visual Basic) et qui ciblent .NET Framework et Windows 10 en code natif.  
  
 En règle générale, les applications qui ciblent .NET Framework sont compilées en langage intermédiaire (IL). Au moment de l'exécution, le compilateur juste-à-temps (JIT) traduit le langage intermédiaire en code natif. En revanche, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compile les applications Windows directement en code natif. Pour les développeurs, cela signifie les points suivants :  
  
-   Vos applications tireront pleinement parti du code natif.  
  
-   Vous pouvez continuer à programmer en C# ou Visual Basic.  
  
-   Vous pouvez continuer à exploiter les ressources fournies par .NET Framework, y compris sa bibliothèque de classes, la gestion automatique de la mémoire, le garbage collection et la gestion des exceptions.  
  
 Pour les utilisateurs de vos applications, [!INCLUDE[net_native](../../../includes/net-native-md.md)] présente les avantages suivants :  
  
-   Temps d'exécution rapides  
  
-   Temps de démarrage systématiquement rapide  
  
-   Faibles coûts de déploiement et de mise à jour  
  
-   Utilisation optimisée de la mémoire par les applications  
  
 Toutefois, [!INCLUDE[net_native](../../../includes/net-native-md.md)] va au-delà d'une simple compilation en code natif. Il transforme la façon dont les applications .NET Framework sont intégrées et exécutées. En particulier :  
  
-   Pendant la précompilation, les parties nécessaires de .NET Framework sont liées statiquement dans votre application. Cela permet à l'application de s'exécuter avec les bibliothèques app-local de .NET Framework et au compilateur d'effectuer une analyse globale pour procurer des gains de performance. Ainsi, les applications se lancent systématiquement plus rapidement même après une mise à jour de .NET Framework.  
  
-   Le runtime [!INCLUDE[net_native](../../../includes/net-native-md.md)] est optimisé pour la précompilation statique et est donc en mesure d'offrir des performances supérieures. Dans le même temps, il conserve les fonctionnalités de réflexion principales, si productives au regard des développeurs.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] utilise le même système principal que le compilateur C++, qui est optimisé pour les scénarios de précompilation statique.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] peut procurer aux développeurs de code managé les performances de C++, car il s'appuie pratiquement sur les mêmes outils que C++, comme indiqué dans le tableau ci-après.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Bibliothèques|.NET Framework + Windows Runtime|Win32 + Windows Runtime|  
|Compilateur|Compilateur d'optimisation UTC|Compilateur d'optimisation UTC|  
|Déployé|Fichiers binaires prêts à être exécutés|Fichiers binaires prêts à être exécutés (ASM)|  
|Exécution|MRT.dll (Runtime CLR minimal)|CRT.dll (Runtime C)|  
  
 Pour les applications Windows pour Windows 10, vous devez charger les binaires de compilation de code .NET Native contenus dans les packages d’application (fichiers .aspx) vers le Windows Store.  
  
## <a name="in-this-section"></a>Dans cette section  
 Pour plus d'informations sur le développement d'applications avec la compilation de code .NET Native, consultez les rubriques suivantes :  
  
-   [Prise en main de la compilation de code .NET Native : procédure détaillée pour les développeurs](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET Native et compilation :](../../../docs/framework/net-native/net-native-and-compilation.md) Comment .NET Native compile votre projet en code natif.  
  
-   [Réflexion et .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [API qui s’appuient sur la réflexion](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [Guide de référence de l'API de réflexion](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [Sérialisation et métadonnées](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Migration de votre application du Windows Store vers .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [Résolution des problèmes généraux liés à .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a>Voir aussi  
 [FAQ sur .NET Native](http://msdn.microsoft.com/vstudio/dn642499.aspx)

