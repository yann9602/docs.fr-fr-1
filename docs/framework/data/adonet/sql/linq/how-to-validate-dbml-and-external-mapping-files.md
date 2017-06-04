---
title: "Proc&#233;dure&#160;: valider des fichiers de mappage externes et DBML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: valider des fichiers de mappage externes et DBML
Les fichiers de mappage externes et les fichiers .dbml que vous modifiez doivent être validés par rapport à leurs définitions de schéma respectives.  Cette rubrique fournit aux utilisateurs [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] les étapes d'implémentation du processus de validation.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### Pour valider un fichier .dbml ou XML  
  
1.  Dans le menu **Fichier** de Visual Studio, pointez sur **Ouvrir**, puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier**, cliquez sur le fichier .dbml ou le fichier de mappage XML que vous souhaitez valider.  
  
     Le fichier s'ouvre dans l'**Éditeur XML**.  
  
3.  Cliquez avec le bouton droit dans la fenêtre, puis cliquez sur **Propriétés**.  
  
4.  Dans la fenêtre **Propriétés**, cliquez sur le bouton de sélection de la propriété **Schémas**.  
  
     La boîte de dialogue **Schémas XML** s'ouvre.  
  
5.  Notez la définition de schéma en fonction de vos besoins.  
  
    -   DbmlSchema.xsd est la définition de schéma pour valider un fichier .dbml.  Pour plus d'informations, consultez [Génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd est la définition de schéma pour valider un fichier mappage XML externe.  Pour plus d'informations, consultez [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  Dans la colonne **Utilisation** de la ligne de définition de schéma souhaitée, cliquez pour ouvrir la zone de liste déroulante, puis cliquez sur **Utiliser ce schéma**.  
  
     Le fichier de définition de schéma est maintenant associé à votre fichier DBML ou votre fichier mappage XML.  
  
     Assurez\-vous qu'aucune autre définition de schéma n'est sélectionnée.  
  
7.  Dans le menu **Affichage**, cliquez sur **Liste d'erreurs**.  
  
     Déterminez si des erreurs, avertissements ou messages ont été générés.  Si ce n'est pas le cas, le fichier XML est valide par rapport à la définition de schéma.  
  
## Méthode alternative pour fournir la définition de schéma  
 Si pour une raison quelconque le fichier .xsd approprié n'apparaît pas dans la boîte de dialogue **Schémas XML**, vous pouvez télécharger le fichier .xsd à partir d'une rubrique d'aide.  Les étapes suivantes vous aident à enregistrer le fichier téléchargé dans le format Unicode requis par l'Éditeur XML [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
#### Pour copier un fichier de définition de schéma à partir d'une rubrique d'aide  
  
1.  Recherchez la rubrique d'aide qui contient la définition de schéma comme décrit précédemment dans cette rubrique.  
  
    -   Pour les fichiers .dbml, consultez [Génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Pour les fichiers de mappage externes, consultez [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Cliquez sur **Copier le code** pour copier le fichier de code vers le Presse\-papiers.  
  
3.  Lancez le Bloc\-notes pour créer un nouveau fichier.  
  
4.  Collez le code du Presse\-papiers dans un fichier Bloc\-notes.  
  
5.  Dans le menu **Fichier** du Bloc\-notes, cliquez sur **Enregistrer sous**.  
  
6.  Dans la zone **Encodage**, sélectionnez **Unicode**.  
  
    > [!IMPORTANT]
    >  Cette sélection garantit que le marqueur d'ordre d'octet Unicode 16 bits \(`FFFE`\) est ajouté au fichier texte.  
  
7.  Dans la zone **Nom de fichier**, créez un nom de fichier avec une extension .xsd.  
  
## Voir aussi  
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)