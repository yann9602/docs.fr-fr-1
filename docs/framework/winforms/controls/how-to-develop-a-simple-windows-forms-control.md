---
title: "Comment&#160;: d&#233;velopper un contr&#244;le Windows Forms simple | Microsoft Docs"
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
  - "Control (classe), Windows Forms"
  - "contrôles (Windows Forms)"
  - "contrôles personnalisés (Windows Forms), créer des contrôles simples à l'aide du code"
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;velopper un contr&#244;le Windows Forms simple
Cette section décrit les étapes essentielles de la création d'un contrôle Windows Forms personnalisé.  Le contrôle simple développé à l'aide de cette procédure permet de modifier l'alignement de sa propriété <xref:System.Windows.Forms.Control.Text%2A>.  Il ne déclenche ou ne gère aucun événement.  
  
### Pour créer un contrôle personnalisé simple  
  
1.  Définissez une classe qui dérive de <xref:System.Windows.Forms.Control?displayProperty=fullName>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  Définissez les propriétés.  \(Vous n'êtes pas obligé de définir les propriétés, car un contrôle hérite de nombreuses propriétés de la classe <xref:System.Windows.Forms.Control>, mais la plupart des contrôles personnalisés définissent généralement des propriétés supplémentaires.\) Le fragment de code suivant définit une propriété appelée `TextAlignment`  qui utilise `FirstControl`  pour mettre en forme l'affichage de la propriété <xref:System.Windows.Forms.Control.Text%2A> héritée de <xref:System.Windows.Forms.Control>.  Pour plus d'informations sur la définition des propriétés, consultez [Properties Overview](../Topic/Properties%20Overview.md).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Lorsque vous définissez une propriété qui modifie l'affichage du contrôle, vous devez appeler la méthode <xref:System.Windows.Forms.Control.Invalidate%2A> pour redessiner le contrôle.  <xref:System.Windows.Forms.Control.Invalidate%2A> est défini dans la classe de base <xref:System.Windows.Forms.Control>.  
  
3.  Substituez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> protégée héritée de <xref:System.Windows.Forms.Control> afin de fournir une logique de rendu à votre contrôle.  Si vous ne substituez pas <xref:System.Windows.Forms.Control.OnPaint%2A>, votre contrôle est incapable de se dessiner.  Dans le fragment de code suivant, la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> affiche la propriété <xref:System.Windows.Forms.Control.Text%2A> héritée de <xref:System.Windows.Forms.Control> avec l'alignement spécifié par le champ `alignmentValue`.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Fournissez des attributs pour votre contrôle.  Les attributs permettent à un concepteur visuel d'afficher correctement votre contrôle ainsi que ses propriétés et événements au moment du design.  Le fragment de code suivant applique des attributs à la propriété `TextAlignment`.  Dans un concepteur tel que Visual Studio .NET, l'attribut <xref:System.ComponentModel.CategoryAttribute.Category%2A> \(repris dans le fragment de code\) entraîne l'affichage de la propriété sous une catégorie logique.  L'attribut <xref:System.ComponentModel.DescriptionAttribute.Description%2A> entraîne l'affichage d'une chaîne descriptive en bas de la fenêtre **Propriétés** lorsque la propriété `TextAlignment` est sélectionnée.  Pour plus d'informations sur les attributs, consultez [Design\-Time Attributes for Components](../Topic/Design-Time%20Attributes%20for%20Components.md).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  \(facultatif\) Fournissez des ressources pour votre contrôle.  Vous pouvez fournir une ressource, telle qu'une bitmap, pour votre contrôle en utilisant une option de compilateur \(`/res`pour C\#\) pour empaqueter des ressources avec votre contrôle.  Au moment de l'exécution, la ressource peut être récupérée à l'aide des méthodes de la classe <xref:System.Resources.ResourceManager>.  Pour plus d'informations sur la création et l'utilisation des ressources, consultez [Ressources dans des applications de bureau](../../../../docs/framework/resources/index.md).  
  
6.  Compilez et déployez votre contrôle.  Pour compiler et déployer `FirstControl,` exécutez les étapes suivantes :  
  
    1.  Enregistrez le code de l'exemple suivant dans un fichier source \(tel que FirstControl.cs ou FirstControl.vb\).  
  
    2.  Compilez le code source dans un assembly et enregistrez\-le dans le répertoire de votre application.  Dans ce but, exécutez la commande suivante à partir du répertoire qui contient le fichier source.  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         L'option de compilateur `/t:library` indique au compilateur que l'assembly que vous créez est une bibliothèque \(et non un exécutable\).  L'option `/out` spécifie le chemin d'accès et le nom de l'assembly.  L'option `/r` fournit le nom des assemblys référencés par votre code.  Dans cet exemple, vous créez un assembly privé que seules vos applications peuvent utiliser.  Vous devez donc l'enregistrer dans le répertoire de votre application.  Pour plus d'informations sur l'empaquetage et le déploiement d'un contrôle pour la distribution, consultez [déploiement](../../../../docs/framework/deployment/net-framework-and-applications.md).  
  
 L'exemple suivant montre le code pour `FirstControl`.  Le contrôle est inséré dans l'espace de noms `CustomWinControls`.  Un espace de noms fournit un regroupement logique des types connexes.  Vous pouvez créer votre contrôle dans un nouvel espace de noms ou dans un espace de noms existant.  En C\#, la déclaration `using` \(`Imports` en Visual Basic\) permet d'accéder aux types à partir d'un espace de noms sans utiliser le nom qualifié complet du type.  Dans l'exemple suivant, la déclaration `using` permet au code d'accéder à la classe <xref:System.Windows.Forms.Control> à partir de <xref:System.Windows.Forms?displayProperty=fullName> simplement en tant que <xref:System.Windows.Forms.Control> au lieu de devoir utiliser le nom qualifié complet <xref:System.Windows.Forms.Control?displayProperty=fullName>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## Utilisation du contrôle personnalisé dans un formulaire  
 L'exemple suivant montre un formulaire simple qui utilise `FirstControl`.  Il crée trois instances de `FirstControl`, chacune possédant une valeur différente pour la propriété `TextAlignment`.  
  
#### Pour compiler et exécuter cet exemple  
  
1.  Enregistrez le code de l'exemple suivant dans un fichier source \(SimpleForm.cs ou SimpleForms.vb\).  
  
2.  Compilez le code source dans un assembly exécutable en lançant la commande suivante à partir du répertoire qui contient le fichier source.  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll est l'assembly qui contient la classe `FirstControl`.  Cet assembly doit se trouver dans le même répertoire que le fichier source du formulaire qui y accède \(SimpleForm.cs ou SimpleForms.vb\).  
  
3.  Exécutez SimpleForm.exe à l'aide de la commande suivante.  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## Voir aussi  
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)