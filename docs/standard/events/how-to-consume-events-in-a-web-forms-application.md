---
title: "Comment&#160;: consommer des &#233;v&#233;nements dans une application Web Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements (.NET Framework), Web Forms"
  - "Web Forms (contrôles), et événements"
  - "gestionnaire d’événements (.NET Framework), Web Forms"
  - "événements (.NET Framework), consommation"
  - "Web Forms, gestion des événements"
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: consommer des &#233;v&#233;nements dans une application Web Forms
Un scénario courant dans les applications Web Forms ASP.NET est de remplir une page Web de contrôles, puis d'exécuter une action spécifique selon le contrôle sur lequel l'utilisateur clique.  Par exemple, un contrôle <xref:System.Web.UI.WebControls.Button?displayProperty=fullName> déclenche un événement lorsque l'utilisateur clique dessus dans la page Web.  En gérant l'événement, votre application peut exécuter la logique d'application appropriée à un clic sur ce bouton.  
  
### Pour gérer un événement Click du bouton dans une page Web  
  
1.  Créez une page Web Forms ASP.NET \(page Web\) dont le contrôle <xref:System.Web.UI.WebControls.Button> avec la valeur `OnClick` définie sur le nom de la méthode que vous allez à l'étape suivante.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Définir un gestionnaire d'événements qui correspond à la signature délégué d'événement <xref:System.Web.UI.WebControls.Button.Click> et qui a le nom que vous avez défini pour la valeur `OnClick`.  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     L'événement <xref:System.Web.UI.WebControls.Button.Click> utilise la classe <xref:System.EventHandler> pour le type délégué et la classe <xref:System.EventArgs> pour les données d'événement.  L'infrastructure de page ASP.NET génère du code qui crée une instance <xref:System.EventHandler> qui référence et ajoute cette instance de délégué à l'événement <xref:System.Web.UI.WebControls.Button.Click> de l'instance de Button <xref:System.Web.UI.WebControls.Button>.  
  
3.  En cas de la méthode du gestionnaire que vous avez définie à l'étape 2, ajoutez un code pour exécuter toutes les actions requises lorsque l'événement se produit.  
  
## Voir aussi  
 [Événements](../../../docs/standard/events/index.md)