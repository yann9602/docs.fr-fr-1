---
title: "XML to Schema Wizard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlToSchemaWizard"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
  - "XML schemas, creating"
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML to Schema Wizard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Utilisez l'Assistant Schéma XML vers pour créer un jeu de schémas XML qui est déduit d'un ou plusieurs documents XML et l'inclure dans votre projet.  Vous pouvez utiliser toute combinaison de documents XML sous forme de fichiers texte, de flux XML disponibles via une adresse Internet HTTP ou de code XML tapé ou collé dans l'Assistant Schéma XML vers.  
  
 Les schémas XML sont utilisés pour fournir IntelliSense aux propriétés XML dans Visual Basic.  Pour plus d'informations, consultez [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) et [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).  
  
> [!NOTE]
>  Avant d'exécuter l'Assistant Schéma XML vers, il est recommandé de supprimer tous les fichiers XSD existants du projet générés précédemment par l'Assistant.  Si vous déduisez un jeu de schémas XML correspondant à un jeu de schémas existant, un conflit peut se produire et [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne sera pas en mesure de fournir IntelliSense pour les propriétés XML.  
  
 L'Assistant Schéma XML vers utilise la classe <xref:System.Xml.Schema.XmlSchemaInference> pour créer le schéma pour le code XML fourni.  En conséquence, plusieurs fichiers de schéma peuvent être créés pour le jeu de schémas.  Pour chaque espace de noms XML dans le code XML fourni, un fichier XSD \(Extensible Schema Definition\) est créé.  Pour plus d'informations, consultez la méthode <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>.  
  
 Pour accéder à l'Assistant Schéma XML vers, cliquez sur **Ajouter un nouvel élément** dans le menu **Projet** et ajoutez un modèle **Schéma XML vers** à partir du groupe de modèles **Données** ou **Éléments communs**.  Après avoir inclus toutes les sources de document XML à partir desquelles déduire le jeu de Schémas XML, cliquez sur **OK** pour créer le jeu de schémas déduit.  
  
 **Type de source**  
 Cette colonne affiche le type de la source de document XML : **Fichier**, **URL** ou **XML**.  
  
 **Emplacement du document XML**  
 Cette colonne affiche le chemin d'accès du document XML.  Pour les documents XML tapés ou collés, affiche le contenu du document XML.  
  
 **Ajouter à partir d'un fichier**  
 Cliquez sur ce bouton pour ajouter des fichiers document XML à l'aide de l'Explorateur de fichiers.  
  
 **Ajouter à partir du Web**  
 Cliquez sur ce bouton pour fournir l'adresse HTTP d'un document XML.  
  
 **Entrer ou coller du code XML**  
 Cliquez sur ce bouton pour taper ou coller un document XML dans la boîte de dialogue.  
  
## Voir aussi  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)