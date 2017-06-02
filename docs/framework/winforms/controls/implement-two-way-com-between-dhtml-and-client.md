---
title: "Comment&#160;: impl&#233;menter la communication bidirectionnelle entre le code DHTML et le code d&#39;application cliente | Microsoft Docs"
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
  - "WebBrowser.ObjectForScripting"
  - "WebBrowser.Document"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "communications, DHTML et applications clientes"
  - "DHTML, incorporer dans Windows Forms"
  - "exemples (Windows Forms), WebBrowser (contrôle)"
  - "WebBrowser (contrôle Windows Forms), communication entre DHTML et les applications clientes"
  - "WebBrowser (contrôle Windows Forms), exemples"
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: impl&#233;menter la communication bidirectionnelle entre le code DHTML et le code d&#39;application cliente
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour ajouter du code d'application web dynamique HTML \(DHTML\) existant à vos applications clientes Windows Forms.  Cela est utile quand vous avez consacré beaucoup de temps de développement à la création de contrôles DHTML et que vous souhaitez tirer parti des fonctionnalités d'interface utilisateur enrichies des Windows Forms sans avoir à réécrire le code existant.  
  
 Le contrôle <xref:System.Windows.Forms.WebBrowser> vous permet d'implémenter la communication bidirectionnelle entre votre code d'application cliente et votre code de script de page web par le biais des propriétés <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> et <xref:System.Windows.Forms.WebBrowser.Document%2A>.  Vous pouvez aussi configurer le contrôle <xref:System.Windows.Forms.WebBrowser> pour que vos contrôles web fusionnent de façon homogène avec d'autres contrôles sur votre formulaire d'application, en masquant leur implémentation DHTML.  Pour fusionner les contrôles de façon homogène, mettez en forme la page affichée pour que sa couleur d'arrière\-plan et le style visuel correspondent au reste du formulaire et utilisez les propriétés <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> et <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> pour désactiver les fonctionnalités standard du navigateur.  
  
### Pour incorporer du code DHTML dans votre application Windows Forms  
  
1.  Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> du contrôle <xref:System.Windows.Forms.WebBrowser> pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'ouvrir les fichiers qui sont déposés dessus.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher son menu contextuel quand l'utilisateur clique dessus avec le bouton droit de la souris.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> de répondre aux touches de raccourci.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Définissez la propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> dans le constructeur du formulaire ou un gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  
  
     Le code suivant utilise la classe de formulaire proprement dite pour l'objet de script.  
  
    > [!NOTE]
    >  Le modèle COM \(Component Object Model\) doit pouvoir accéder à l'objet de script.  Pour rendre votre formulaire visible par COM, ajoutez l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> à votre classe de formulaire.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Implémentez dans votre code d'application des propriétés ou des méthodes publiques que votre code de script utilisera.  
  
     Par exemple, si vous utilisez la classe de formulaire pour l'objet de script, ajoutez le code suivant à votre classe de formulaire.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Utilisez l'objet `window.external` dans votre code de script pour accéder aux propriétés et aux méthodes publiques de l'objet spécifié.  
  
     Le code HTML suivant montre comment appeler une méthode sur l'objet de script à partir d'un clic de bouton.  Copiez ce code dans l'élément BODY d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  Implémentez dans votre code de script des fonctions que votre code d'application utilisera.  
  
     L'élément HTML SCRIPT suivant fournit un exemple de fonction.  Copiez ce code dans l'élément HEAD d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Utilisez la propriété <xref:System.Windows.Forms.WebBrowser.Document%2A> pour accéder au code de script à partir de votre code d'application cliente.  
  
     Par exemple, ajoutez le code suivant à un gestionnaire d'événements de bouton <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Quand vous avez terminé de déboguer votre code DHTML, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher des messages d'erreur pour les problèmes de code de script.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## Exemple  
 L'exemple de code complet suivant fournit une application de démonstration que vous pouvez utiliser pour comprendre cette fonctionnalité.  Le code HTML est chargé dans le contrôle <xref:System.Windows.Forms.WebBrowser> via la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> au lieu d'être chargé à partir d'un fichier HTML distinct.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## Compilation du code  
 Ce code nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=fullName>   
 [WebBrowser, contrôle](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)