---
title: "Assistant XML vers schéma (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlToSchemaWizard
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
- XML schemas, creating
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
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
ms.openlocfilehash: d0c9c0247f3d9934ef973c7322cb098f9b445a5a
ms.lasthandoff: 03/13/2017

---
# <a name="xml-to-schema-wizard-visual-basic"></a>Assistant XML vers schéma (Visual Basic)
Utilisez l’Assistant schéma XML vers pour créer un jeu de schémas XML qui est déduit à partir d’un ou plusieurs documents XML et l’inclure dans votre projet. Vous pouvez utiliser n’importe quelle combinaison de documents XML sous la forme de fichiers texte, XML à partir d’une adresse HTTP Internet ou code XML tapé ou collé dans l’Assistant schéma XML vers.  
  
 Schémas XML sont utilisés pour fournir IntelliSense pour les propriétés XML en Visual Basic. Pour plus d’informations, consultez [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) et [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).  
  
> [!NOTE]
>  Avant d’exécuter le code XML à l’Assistant schéma, il est recommandé de supprimer tous les fichiers XSD existants du projet qui ont été précédemment généré par l’Assistant. Si vous déduisez un jeu de schémas XML qui correspond à un jeu de schémas existant, un conflit peut se produire et [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne sera pas en mesure de fournir IntelliSense pour les propriétés XML.  
  
 L’Assistant schéma XML vers utilise la <xref:System.Xml.Schema.XmlSchemaInference>classe pour créer le schéma pour le code XML fourni.</xref:System.Xml.Schema.XmlSchemaInference> Par conséquent, plusieurs fichiers de schéma peuvent être créés pour le jeu de schémas. Pour chaque espace de noms XML dans le code XML fourni, un fichier Extensible XSD (Schema Definition) est créé. Pour plus d’informations, consultez la <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>méthode.</xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>  
  
 Pour accéder à l’Assistant schéma XML vers, cliquez sur **ajouter un nouvel élément** sur la **projet** menu et ajoutez un **XML au schéma** modèle à partir de le le **données** ou **éléments communs** groupe de modèles. Une fois que vous avez inclus toutes les sources de document XML pour déduire le jeu de schémas XML à partir de, cliquez sur **OK** pour créer le schéma déduit jeu.  
  
 **Type de source**  
 Cette colonne affiche le type de source du document XML : **fichier**, **URL**, ou **XML**.  
  
 **Emplacement du Document XML**  
 Cette colonne affiche le chemin d’accès du document XML. Pour les documents XML tapés ou collés, affiche le contenu du document XML.  
  
 **Ajouter à partir du fichier**  
 Cliquez sur ce bouton pour ajouter des fichiers de documents XML à l’aide de l’Explorateur de fichiers.  
  
 **Ajouter à partir du Web**  
 Cliquez sur ce bouton pour fournir l’adresse HTTP d’un document XML.  
  
 **Tapez ou collez le XML**  
 Cliquez sur ce bouton pour taper ou coller un document XML dans la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Schema.XmlSchemaInference></xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)
