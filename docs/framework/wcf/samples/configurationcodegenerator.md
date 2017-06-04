---
title: "ConfigurationCodeGenerator | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# ConfigurationCodeGenerator
Le ConfigurationCodeGenerator est un outil que vous pouvez utiliser pour exposer vos implémentations de canal personnalisées au système de configuration.Cela permet aux utilisateurs de votre canal personnalisé de configurer votre canal en utilisant un fichier .config comme ils configureraient une liaison fournie par le système telle que `NetTcpBinding` ou une liaison personnalisée à l'aide de `TcpTransportBindingElement`.  
  
 Lorsque vous écrivez un canal personnalisé et l'exposez au modèle de programmation en utilisant un nouveau `BindingElement` ou une `Binding`, vous devez créer un ensemble de classes pour rendre le `BindingElement` ou la `Binding` configurable à l'aide d'un fichier .config.Vous pouvez utiliser l'outil ConfigurationCodeGenerator pour générer ces classes et améliorer l'expérience de votre client.  
  
### Pour générer l'outil  
  
1.  Pour générer la solution, suivez les instructions indiquées dans la rubrique [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  La génération de la solution génère un fichier : ConfigurationCodeGenerator.exe.Le fichier SampleRun.cmd comprend un exemple ligne de commande qui indique comment utiliser cet outil pour générer les classes pour l'exemple [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
### Pour exécuter l'outil  
  
1.  Dans l'invite de commandes, tapez ce qui suit si vous avez à la fois un type `BindingElement` personnalisé et un type `Binding` personnalisé :  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
  
    ```  
  
     Ou tapez ce qui suit si vous avez uniquement un type `BindingElement` personnalisé :  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
  
    ```  
  
     Ou tapez ce qui suit si vous avez uniquement un type `Binding` personnalisé :  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
  
    ```  
  
     La commande génère trois fichiers .cs pour le `BindingElement` \(si vous avez spécifié l'option \/be:\), cinq fichiers .cs pour la `Binding` standard \(si vous avez spécifié l'option \/sb:\), et un fichier .xml.  
  
    1.  Si vous avez utilisé l'option \/be, l'un des fichiers .cs implémente `BindingElementExtensionSection` pour votre élément de liaison.Ce code expose votre `BindingElement` au système de configuration, afin que d'autres liaisons personnalisées puissent utiliser votre élément de liaison.Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes.Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.  
  
    2.  Si vous avez spécifié l'option \/sb, deux des fichiers .cs implémentent respectivement un `StandardBindingElement` et un `StandardBindingCollectionElement`, qui expose votre liaison standard au système de configuration.Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes.Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.  
  
         Si vous avez spécifié l'option \/sb:, le CodeToAddTo\<*YourStdBinding*\>.cs comprend un code que vous devez ajouter manuellement à la classe qui implémente votre liaison standard.  
  
     Le fichier SampleConfig.xml contient le code de configuration que vous devez ajouter au fichier de configuration qui enregistre les gestionnaires définis à l'étape 1 ou 2 précédente.  
  
## Voir aussi