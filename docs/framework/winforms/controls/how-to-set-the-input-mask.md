---
title: "Comment&#160;: d&#233;finir le masque de saisie | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.MaskPropertyEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MaskedTextBox (contrôle Windows Forms)"
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: d&#233;finir le masque de saisie
Le contrôle de zone de texte masqué est un contrôle de zone de texte amélioré qui prend en charge une syntaxe déclarative pour accepter ou rejeter l'entrée d'utilisateur.  En définissant la propriété Masque, vous pouvez spécifier l'entrée d'utilisateur autorisée sans écrire de logique de validation personnalisée dans votre application.  Pour plus d'informations, consultez la section Notes de la classe <xref:System.Windows.Forms.MaskedTextBox>.  
  
## Définition manuelle de la propriété Masque  
 Si vous êtes familiarisé avec les caractères que la propriété Masque prend en charge, vous pouvez saisir cette dernière manuellement.  Pour obtenir un résumé des caractères que la propriété Masque prend en charge, consultez la section Notes de la propriété <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>.  
  
#### Pour définir la propriété Masque manuellement  
  
1.  En mode **Design**, sélectionnez une <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  Dans la fenêtre **Propriétés**, recherchez la propriété <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>.  
  
3.  Saisissez le masque que vous souhaitez.  Par exemple, tapez `###`.  
  
## Utilisation de la boîte de dialogue Masque de saisie  
 La boîte de dialogue Masque de saisie fournit des masques de saisie prédéfinis.  Vous pouvez également modifier les masques prédéfinis ou entrer votre propre masque manuellement.  
  
#### Pour ouvrir la boîte de dialogue Masque de saisie  
  
1.  En mode **Design**, sélectionnez une <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Cliquez sur la balise active pour ouvrir le panneau **Tâches MaskedTextBox**.  
  
    2.  Cliquez sur **Définir le masque**.  
  
     \- ou \-  
  
    1.  Dans la fenêtre **Propriétés**, sélectionnez la propriété <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>.  
  
    2.  Cliquez sur le bouton de sélection dans la colonne Valeur de la propriété.  
  
     La boîte de dialogue **Masque de saisie** apparaît.  
  
#### Pour utiliser la boîte de dialogue Masque de saisie  
  
1.  \(Facultatif\) Cliquez sur l'un des masques prédéfinis dans la liste.  
  
2.  \(Facultatif\) Modifiez le masque prédéfini dans la zone **Masque**.  
  
3.  \(Facultatif\) Saisissez un nouveau masque dans la zone **Masque**.  Autrement dit, vous n'avez pas à utiliser l'un des masques prédéfinis.  
  
    > [!NOTE]
    >  La zone Aperçu affiche les caractères que l'utilisateur voit dans la <xref:System.Windows.Forms.MaskedTextBox>.  Ces caractères aident l'utilisateur à entrer les données correctement.  
  
4.  Activez ou désactivez la case à cocher **Utiliser ValidatingType**.  La case à cocher **Utiliser ValidatingType** spécifie si l'utilisateur se sert d'un type de données pour vérifier l'entrée de données.  Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.  
  
5.  Cliquez sur **OK**.  
  
     Le masque est entré dans la propriété **Masque** de la fenêtre **Propriétés**.  
  
## Voir aussi  
 [Procédure pas à pas : utilisation du contrôle MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)