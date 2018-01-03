---
title: "Comment : valider des fichiers de mappage externes et DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9339176cbc6a72d940e3fa053c0e54e0667193f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Comment : valider des fichiers de mappage externes et DBML
Les fichiers de mappage externes et les fichiers .dbml que vous modifiez doivent être validés par rapport à leurs définitions de schéma respectives. Cette rubrique fournit aux utilisateurs [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] les étapes d'implémentation du processus de validation.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Pour valider un fichier .dbml ou XML  
  
1.  Dans Visual Studio **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **fichier**.  
  
2.  Dans le **ouvrir le fichier** boîte de dialogue, cliquez sur le fichier .dbml ou le fichier de mappage XML que vous souhaitez valider.  
  
     Le fichier s’ouvre dans le **éditeur XML**.  
  
3.  Avec le bouton droit de la fenêtre, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection pour la **schémas** propriété.  
  
     Le **schémas XML** boîte de dialogue s’ouvre.  
  
5.  Notez la définition de schéma en fonction de vos besoins.  
  
    -   DbmlSchema.xsd est la définition de schéma pour valider un fichier .dbml. Pour plus d’informations, consultez [la génération de Code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd est la définition de schéma pour valider un fichier mappage XML externe. Pour plus d’informations, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  Dans le **utilisez** colonne de la ligne de définition de schéma de votre choix, cliquez pour ouvrir la zone de liste déroulante, puis cliquez sur **utiliser ce schéma**.  
  
     Le fichier de définition de schéma est maintenant associé à votre fichier DBML ou votre fichier mappage XML.  
  
     Assurez-vous qu'aucune autre définition de schéma n'est sélectionnée.  
  
7.  Sur le **vue** menu, cliquez sur **liste d’erreurs**.  
  
     Déterminez si des erreurs, avertissements ou messages ont été générés. Si ce n'est pas le cas, le fichier XML est valide par rapport à la définition de schéma.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Méthode alternative pour fournir la définition de schéma  
 Si pour une raison quelconque le .xsd approprié fichier n’apparaît pas dans le **schémas XML** boîte de dialogue, vous pouvez télécharger le fichier .xsd à partir d’une rubrique d’aide. Les étapes suivantes vous aident à enregistrer le fichier téléchargé dans le format Unicode requis par l'Éditeur XML [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Pour copier un fichier de définition de schéma à partir d'une rubrique d'aide  
  
1.  Recherchez la rubrique d'aide qui contient la définition de schéma comme décrit précédemment dans cette rubrique.  
  
    -   Pour les fichiers .dbml, consultez [la génération de Code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Pour les fichiers de mappage externe, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Cliquez sur **copier le Code** pour copier le fichier de code dans le Presse-papiers.  
  
3.  Lancez le Bloc-notes pour créer un nouveau fichier.  
  
4.  Collez le code du Presse-papiers dans un fichier Bloc-notes.  
  
5.  Dans le bloc-notes **fichier** menu, cliquez sur **Enregistrer sous**.  
  
6.  Dans le **codage** boîte, sélectionnez **Unicode**.  
  
    > [!IMPORTANT]
    >  Cette sélection garantit que le marqueur d'ordre d'octet Unicode 16 bits (`FFFE`) est ajouté au fichier texte.  
  
7.  Dans le **nom de fichier** zone, créez un nom de fichier avec une extension .xsd.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
