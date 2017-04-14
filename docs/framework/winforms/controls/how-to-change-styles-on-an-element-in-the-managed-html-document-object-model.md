---
title: "Comment&#160;: modifier des styles d&#39;un &#233;l&#233;ment dans le mod&#232;le objet de document HTML manag&#233; | Microsoft Docs"
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
  - "modèle DOM HTML managé, modifier les styles d'éléments"
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: modifier des styles d&#39;un &#233;l&#233;ment dans le mod&#232;le objet de document HTML manag&#233;
Vous pouvez utiliser des styles dans du HTML pour contrôler l'apparence d'un document et de ses éléments.  <xref:System.Windows.Forms.HtmlDocument> et <xref:System.Windows.Forms.HtmlElement> prennent en charge des propriétés <xref:System.Windows.Forms.HtmlElement.Style%2A> qui prennent des chaînes de style au format suivant :  
  
 `name1:value1;...;nameN:valueN;`  
  
 Voici `DIV` avec une chaîne de style qui spécifie l'utilisation de la police Arial et l'affichage de la totalité du texte en gras :  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 La difficulté que présente la manipulation de styles à l'aide de la propriété <xref:System.Windows.Forms.HtmlElement.Style%2A> réside dans le fait que l'ajout et la suppression de paramètres de style individuels peuvent s'avérer fastidieux.  Par exemple, la procédure deviendrait complexe s'il fallait restituer le texte précédent en italique chaque fois que l'utilisateur place le curseur sur `DIV` et supprimer les caractères en italique lorsque le curseur sort de `DIV`.  La manipulation d'un grand nombre de styles de cette façon prendrait trop de temps.  
  
 La procédure suivante contient un code que vous pouvez utiliser pour manipuler facilement des styles dans des documents HTML et dans des éléments.  Pour exécuter cette procédure, vous devez maîtriser certaines tâches de base dans les Windows Forms, telles que la création d'un nouveau projet et l'ajout d'un contrôle à un formulaire.  
  
### Pour traiter des modifications de style dans une application Windows Forms  
  
1.  Créez un projet Windows Forms.  
  
2.  Créez un fichier de classe avec l'extension appropriée pour votre langage de programmation.  
  
3.  Copiez le code de classe `StyleGenerator` contenu dans la section Exemple de cette rubrique dans le fichier de classe, puis enregistrez ce code.  
  
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
  
5.  Ajoutez un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` au formulaire principal de votre projet.  
  
6.  Ajoutez le code suivant au fichier de code de votre projet.  
  
    > [!IMPORTANT]
    >  Vérifiez que le gestionnaire d'événements `webBrowser1_DocumentCompleted` est configuré comme écouteur pour l'événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>.  Dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double\-cliquez sur le contrôle <xref:System.Windows.Forms.WebBrowser> ; dans un éditeur de texte, configurez l'écouteur par programme.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Exécutez le projet.  Placez votre curseur sur le premier `DIV` afin d'observer les effets du code.  
  
## Exemple  
 L'exemple de code suivant affiche le code complet pour la classe `StyleGenerator`, qui analyse une valeur de style existante, prend en charge l'ajout, la modification et la suppression de styles, et retourne une nouvelle valeur de style contenant les modifications demandées.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.HtmlElement>