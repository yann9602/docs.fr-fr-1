---
title: "Comment&#160;: &#233;tablir une liaison &#224; un service Web &#224; l&#39;aide du BindingSource Windows Forms | Microsoft Docs"
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
  - "BindingSource (composant Windows Forms), lier à un service Web"
  - "BindingSource (composant Windows Forms), exemples"
  - "contrôles (Windows Forms), lier au service Web"
  - "exemples (Windows Forms), BindingSource (composant)"
  - "services Web, lier des contrôles"
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# Comment&#160;: &#233;tablir une liaison &#224; un service Web &#224; l&#39;aide du BindingSource Windows Forms
Si vous voulez lier un contrôle Windows Forms aux résultats obtenus à partir d'un appel à un service web XML, vous pouvez utiliser un composant <xref:System.Windows.Forms.BindingSource>.  Cette procédure est similaire à celle d'une liaison d'un composant <xref:System.Windows.Forms.BindingSource> à un type.  Vous devez créer un proxy côté client qui contienne les méthodes et les types exposés par le service web.  Vous générez un proxy côté client à partir du service web \(.asmx\) lui\-même ou à partir de son fichier WSDL.  En outre, votre proxy côté client doit exposer les champs de types complexes utilisés par le service web en tant que propriétés publiques.  Vous pouvez ensuite lier la <xref:System.Windows.Forms.BindingSource> à l'un des types exposés dans le proxy du service web.  
  
### Pour créer un proxy côté client et créer des liaisons à celui\-ci  
  
1.  Créez un formulaire Windows dans le répertoire de votre choix, avec un espace de noms approprié.  
  
2.  Ajoutez un composant <xref:System.Windows.Forms.BindingSource> au formulaire.  
  
3.  Ouvrez l'invite de commandes [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)], puis accédez au répertoire où se trouve votre formulaire.  
  
4.  À l'aide de l'outil WSDL, entrez `wsdl` et l'URL du fichier .asmx ou WSDL du service Web, suivie de l'espace de noms de votre application, et éventuellement le langage utilisé.  
  
     L'exemple de code suivant utilise le service web situé à l'adresse suivante : http:\/\/webservices.eraserver.  net\/zipcoderesolver\/zipcoderesolver.asmx.  Pour obtenir un exemple pour un type C\#, voir `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx BindToWebService`. Pour obtenir un exemple pour un type Visual Basic, voir `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.  Le fait de passer le chemin d'accès en tant qu'argument à l'outil WSDL génère un proxy côté client dans le même répertoire et le même espace de noms que votre application, dans le langage spécifié.  Si vous utilisez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], ajoutez le fichier à votre projet.  
  
5.  Sélectionnez un type dans le proxy côté client avec lequel créer une liaison.  
  
     Il s'agit généralement d'un type retourné par une méthode fournie par le service web.  Les champs du type choisi doivent être exposés en tant que propriétés publiques pour la liaison.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Définissez la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource> sur le type contenu dans le proxy côté client du service web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### Pour lier des contrôles à une BindingSource liée à un service web  
  
-   Liez des contrôles à <xref:System.Windows.Forms.BindingSource>, en passant la propriété publique du type de service web de votre choix en tant que paramètre.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## Exemple  
 L'exemple de code suivant montre comment lier un composant <xref:System.Windows.Forms.BindingSource> à un service web, puis comment lier une zone de texte au composant <xref:System.Windows.Forms.BindingSource>.  Quand vous cliquez sur le bouton, une méthode de service web est appelée et les résultats s'affichent dans `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## Compilation du code  
 Il s'agit d'un exemple complet qui inclut une méthode `Main` et une version raccourcie du code du proxy côté client.  
  
 Cet exemple nécessite :  
  
-   Des références aux assemblys System, System.Drawing, System.Web.Services, System.Windows.Forms et System.Xml.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], voir [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Voir également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)