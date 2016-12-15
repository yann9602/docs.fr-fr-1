---
title: "Errors occurred while compiling the XML schemas in the project | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36810"
  - "vbc36810"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36810"
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Errors occurred while compiling the XML schemas in the project
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Des erreurs se sont produites lors de la compilation des schémas XML du projet.De ce fait, XML IntelliSense n'est pas disponible.  
  
 Il existe une erreur dans une définition de schéma XML incluse dans le projet.  Cette erreur se produit lorsque vous ajoutez un fichier de schéma XSD \(.xsd\) qui est en conflit avec le jeu de schémas XSD existant pour le projet.  
  
 **ID d'erreur :** BC36810  
  
### Pour corriger cette erreur  
  
-   Double\-cliquez sur l'avertissement dans la fenêtre **Liste d'erreurs**.  Visual Basic vous conduit à l'emplacement dans le fichier XSD correspondant à la source de l'avertissement.  Corrigez l'erreur dans le schéma XSD.  
  
-   Vérifiez que tous les fichiers du schéma XSD requis \(.xsd\) sont inclus dans le projet.  Vous devrez peut\-être cliquer sur **Afficher tous les fichiers** dans le menu **Projet** pour afficher vos fichiers .xsd dans l'**Explorateur de solutions**.  Cliquez avec le bouton droit sur un fichier .xsd, puis cliquez sur **Inclure dans le projet** pour inclure le fichier dans votre projet.  
  
-   Si vous utilisez l'Assistant Schéma XML vers, cette erreur peut se produire si vous déduisez des schémas à plusieurs reprises à partir de la même source.  Dans ce cas, vous pouvez supprimer les fichiers de schéma XSD existants du projet, ajouter un nouveau modèle d'élément Schéma XML vers, puis fournir l'Assistant Schéma XML vers avec toutes les sources XML applicables à votre projet.  
  
-   Si aucune erreur n'est identifiée dans votre schéma XSD, il se peut que le compilateur XML ne dispose pas d'informations suffisantes pour fournir un message d'erreur détaillé.  Vous pouvez obtenir davantage d'informations détaillées sur l'erreur si vous vérifiez que les espaces de noms XML pour les fichiers .xsd inclus dans votre projet correspondent aux espaces de noms XML identifiés pour le jeu de schémas XML Visual Studio.  
  
## Voir aussi  
 [Liste d'erreurs, fenêtre](/visual-studio/ide/reference/error-list-window)   
 [XML IntelliSense in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)