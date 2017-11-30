---
title: "Comment : modifier des styles d'un élément dans le modèle objet de document HTML managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968dd4210e13e301ba2f0ca24617df23706cefc0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Comment : modifier des styles d'un élément dans le modèle objet de document HTML managé
Vous pouvez utiliser les styles HTML pour contrôler l’apparence d’un document et ses éléments. <xref:System.Windows.Forms.HtmlDocument>et <xref:System.Windows.Forms.HtmlElement> prennent en charge <xref:System.Windows.Forms.HtmlElement.Style%2A> propriétés qui acceptent des chaînes de style au format suivant :  
  
 `name1:value1;...;nameN:valueN;`  
  
 Voici une `DIV` avec une chaîne de style qui définit la police Arial et tout le texte en gras :  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 Le problème avec la manipulation de styles à l’aide de la <xref:System.Windows.Forms.HtmlElement.Style%2A> propriété est qu’il peut s’avérer fastidieux à et supprimez les paramètres de style à partir de la chaîne. Par exemple, il devient une procédure complexe, vous permettant de restituer le texte précédent en italique chaque fois que l’utilisateur positionne le curseur sur le `DIV`et en italique lorsque le curseur quitte le `DIV`. Temps devient un problème si vous avez besoin manipuler un grand nombre de styles de cette manière.  
  
 La procédure suivante contient le code que vous pouvez utiliser pour manipuler facilement des styles sur les éléments et les documents HTML. La procédure, vous devez savoir comment effectuer des tâches de base dans les Windows Forms, telles que la création d’un projet et ajouter un contrôle à un formulaire.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Pour traiter les modifications de style dans une application Windows Forms  
  
1.  Créez un projet Windows Forms.  
  
2.  Créer un nouveau fichier de classe avec l’extension appropriée pour votre langage de programmation.  
  
3.  Copie le `StyleGenerator` code dans la section exemple de cette rubrique de la classe dans le fichier de classe, puis enregistrez le code.  
  
4.  Enregistrez le code HTML suivant dans un fichier nommé Test.htm.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Ajouter un <xref:System.Windows.Forms.WebBrowser> contrôle nommé `webBrowser1` au formulaire principal de votre projet.  
  
6.  Ajoutez le code suivant au fichier de code de votre projet.  
  
    > [!IMPORTANT]
    >  Vérifiez que le `webBrowser1_DocumentCompleted` Gestionnaire d’événements est configuré en tant qu’écouteur pour le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement. Dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double-cliquez sur le <xref:System.Windows.Forms.WebBrowser> contrôle ; dans un éditeur de texte, configurez l’écouteur par programme.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Exécutez le projet. Exécutez votre curseur sur la première `DIV` pour observer les effets du code.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre le code complet pour le `StyleGenerator` (classe), qui analyse une valeur de style existante, prend en charge Ajout, modification et suppression de styles et retourne une nouvelle valeur de style avec les modifications demandées.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.HtmlElement>
