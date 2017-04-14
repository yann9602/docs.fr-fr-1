---
title: "Exposing .NET Framework Components to COM | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "exposing .NET Framework components to COM"
  - "interoperation with unmanaged code, exposing .NET Framework components"
  - "COM interop, exposing COM components"
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Exposing .NET Framework Components to COM
L'écriture d'un type .NET et la consommation de ce type à partir d'un code non managé sont deux activités distinctes pour les développeurs.  Cette section donne plusieurs conseils d'écriture de code managé interopérant avec des clients COM :  
  
-   [Qualification des types .NET en vue d'une interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Tous les types, méthodes, propriétés, champs et événements managés que vous voulez exposer à COM doivent être publics.  Les types doivent posséder un constructeur public par défaut, seul constructeur pouvant être appelé via COM.  
  
-   [Application d'attributs d'interopérabilité](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Des attributs personnalisés figurant dans du code managé peuvent améliorer l'interopérabilité d'un composant.  
  
-   [Empaquetage d'un assembly pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Les développeurs COM peuvent exiger que vous récapituliez les étapes relatives au référencement et au déploiement de vos assemblys.  
  
 De plus, cette section identifie les tâches relatives à la consommation d'un type managé à partir d'un client COM.  
  
#### Pour consommer un type managé à partir de COM  
  
1.  [Inscrivez les assemblys dans COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Les types figurant dans un assembly \(et des bibliothèques de types\) doivent être inscrits au moment du design.  Si un programme d'installation n'inscrit pas l'assembly, ordonnez alors aux développeurs COM d'utiliser Regasm.exe.  
  
2.  [Référencez des types .NET à partir de COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Les développeurs COM peuvent référencer des types dans un assembly à l'aide des mêmes outils et techniques qu'ils emploient aujourd'hui.  
  
3.  [Appelez un objet .NET](http://msdn.microsoft.com/fr-fr/40c9626c-aea6-4bad-b8f0-c1de462efd33).  
  
     Les développeurs COM peuvent appeler des méthodes sur l'objet .NET de la même manière qu'ils appellent des méthodes sur un type non managé.  Par exemple, l'interface API **CoCreateInstance** COM active les objets .NET.  
  
4.  [Déployez une application pour accéder à COM](http://msdn.microsoft.com/fr-fr/fb63564c-c1b9-4655-a094-a235625882ce).  
  
     Un assembly avec nom fort peut être installé dans le Global Assembly Cache ; il nécessite une signature de son éditeur.  Les assemblys sans nom fort doivent être installés dans le répertoire de l'application du client.  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md)   
 [COM Interop Sample: COM Client and .NET Server](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)