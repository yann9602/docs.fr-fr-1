---
title: "Comment&#160;: ajouter un emplacement personnalis&#233; &#224; une bo&#238;te de dialogue Fichier | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "emplacement personnalisé (boîte de dialogue)"
  - "ajout d'un emplacement personnalisé à une boîte de dialogue"
  - "CustomPlaces (collection)"
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter un emplacement personnalis&#233; &#224; une bo&#238;te de dialogue Fichier
La valeur par défaut ouvrir et enregistrer des boîtes de dialogue sur [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] disposent d’une zone sur le côté gauche de la boîte de dialogue intitulée **liens favoris**. Cette zone est appelée emplacements personnalisés. Le <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> classes permettent d’ajouter des dossiers à la <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.  
  
> [!NOTE]
>  Dans l’ordre d’un emplacement personnalisé à afficher dans le <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, le <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriété doit avoir la valeur `true` (la valeur par défaut).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Pour ajouter un emplacement personnalisé à une boîte de dialogue  
  
-   Ajouter un chemin d’accès, un GUID de dossier connu ou un <xref:System.Windows.Forms.FileDialogCustomPlace> de l’objet à le <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection de la boîte de dialogue.  
  
     L’exemple de code suivant montre comment ajouter un chemin d’accès :  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FileDialog>   
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=fullName>   
 [GUID de dossier connus pour des emplacements personnalisés de boîtes de dialogue fichier](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)