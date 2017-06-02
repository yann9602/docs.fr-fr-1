---
title: "Comment&#160;: cr&#233;er une application Windows Forms &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Forms, développement d'applications à partir de la ligne de commande"
  - "Windows Forms, créer un formulaire de base"
  - "Windows Forms, mise en route"
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une application Windows Forms &#224; partir de la ligne de commande
Les procédures suivantes décrivent les étapes de base que vous devez effectuer pour créer et exécuter une application Windows Forms à partir de la ligne de commande.  Ces procédures sont très bien prises en charge dans Visual Studio.  Consultez également [Procédure pas à pas : création d'un Windows Form simple](http://msdn.microsoft.com/library/z9w2f38k%20\(v=vs.110\)).  
  
## Procédure  
  
#### Pour créer le formulaire  
  
1.  Dans un fichier de code vide, tapez les instructions import ou using suivantes :  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  Déclarez une classe nommée `Form1` qui hérite de la classe Form.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  Créez un constructeur par défaut pour `Form1`.  
  
     Vous ajouterez du code au constructeur lors d'une procédure ultérieure.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  Ajoutez une méthode `Main` à la classe.  
  
    1.  Appliquer le <xref:System.STAThreadAttribute> à la méthode `Main` pour indiquer que votre application Windows Forms est un thread unique cloisonné.  
  
    2.  Appelez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pour donner une apparence Windows XP à votre application.  
  
    3.  Créez une instance du formulaire et exécutez\-la.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### Pour compiler et exécuter l'application  
  
1.  À l'invite de commandes .NET Framework, accédez au répertoire où vous avez créé la classe `Form1`.  
  
2.  Compilez le formulaire.  
  
    -   Si vous utilisez C\#, tapez : `csc form1.cs`  
  
         `ou`  
  
    -   Si vous utilisez Visual Basic, tapez : `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`  
  
3.  À l'invite de commandes, tapez : `Form1.exe`  
  
## Ajout d'un contrôle et gestion d'un événement  
 Les étapes de la procédure précédente illustrent simplement comment créer un Windows Form de base qui se compile et s'exécute.  La procédure suivante illustre comment créer et ajouter un contrôle au formulaire et comment gérer un événement pour le contrôle.  Pour plus d'informations sur les contrôles que vous pouvez ajouter aux Windows Forms, consultez [contrôles Windows Forms](../../../docs/framework/winforms/controls/index.md).  
  
 Outre la création d'applications Windows Forms, vous devez comprendre la programmation basée sur les événements et comment gérer l'entrée d'utilisateur.  Pour plus d'informations, consultez [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md) et [Gestion des entrées utilisateur](../../../docs/framework/winforms/controls/handling-user-input.md).  
  
#### Pour déclarer un contrôle bouton et gérer son événement click  
  
1.  Déclarez un contrôle bouton nommé `button1`.  
  
2.  Dans le constructeur, créez le bouton et définissez ses propriétés <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Text%2A>.  
  
3.  Ajoutez le bouton au formulaire.  
  
     L'exemple de code suivant montre comment déclarer le contrôle bouton.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  Créez une méthode pour gérer l'événement <xref:System.Windows.Forms.Control.Click> pour le bouton.  
  
5.  Dans le gestionnaire d'événements click, affichez un <xref:System.Windows.Forms.MessageBox> avec le message « Hello World ».  
  
     L'exemple de code suivant montre comment gérer l'événement click du contrôle bouton.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  Associez l'événement <xref:System.Windows.Forms.Control.Click> à la méthode que vous avez créée.  
  
     L'exemple de code suivant montre comment associer l'événement à la méthode.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  Compilez et exécutez l'application comme décrit dans la procédure précédente.  
  
## Exemple  
 L'exemple de code suivant constitue l'exemple complet des procédures précédentes.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## Compilation du code  
  
-   Pour compiler le code, suivez les instructions de la procédure précédente qui expliquent comment compiler et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Control>   
 [Modification de l'apparence des Windows Forms](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)   
 [Amélioration des applications Windows Forms](../../../docs/framework/winforms/advanced/index.md)   
 [Mise en route des Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)