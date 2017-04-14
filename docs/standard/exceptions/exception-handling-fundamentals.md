---
title: "Notions de base de la gestion des exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Common Language Runtime, exceptions"
  - "exceptions, exemples"
  - "runtime, exceptions"
ms.assetid: e865d48c-b862-4448-833e-09fcd48adf6b
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Notions de base de la gestion des exceptions
Le Common Language Runtime prend en charge un modèle de gestion des exceptions fondé sur les concepts d'objets exception et de blocs de code protégés.  Le runtime crée un objet pour représenter une exception, lorsque celle\-ci se produit.  Vous pouvez également créer vos propres classes d'exceptions en dérivant des classes à partir de l'exception de base appropriée.  
  
 Tous les langages qui utilisent le runtime gèrent les exceptions de manière similaire.  Chaque langage utilise une forme de gestion des exceptions structurée autour du bloc try\/catch\/finally.  Cette section contient plusieurs exemples de gestion des exceptions de base.  
  
## Dans cette section  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)  
 Décrit la gestion des exceptions à l'aide du bloc try\/catch.  
  
 [Comment : utiliser des exceptions spécifiques dans un bloc catch](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)  
 Décrit comment intercepter des exceptions spécifiques.  
  
 [Comment : lever explicitement des exceptions](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)  
 Décrit comment lever des exceptions et comment intercepter, puis lever de nouveau des exceptions.  
  
 [Comment : créer des exceptions définies par l'utilisateur](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)  
 Indique comment créer vos propres classes d'exceptions.  
  
 [Utilisation de gestionnaires filtrés par l'utilisateur](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)  
 Décrit comment définir des exceptions filtrées.  
  
 [Comment : utiliser un bloc finally](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)  
 Explique comment utiliser l'instruction finally dans un bloc d'exception.  
  
## Rubriques connexes  
 [Exceptions](../../../docs/standard/exceptions/index.md)  
 Donne une vue d'ensemble des exceptions du Common Language Runtime.  
  
 [Classe et propriétés d'exception](../../../docs/standard/exceptions/exception-class-and-properties.md)  
 Décrit les éléments d'un objet exception.