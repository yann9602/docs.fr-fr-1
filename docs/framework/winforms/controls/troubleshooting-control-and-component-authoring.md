---
title: "D&#233;pannage de la cr&#233;ation de contr&#244;les et de composants | Microsoft Docs"
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
  - "composants (Windows Forms), dépanner"
  - "contrôles (Windows Forms), dépanner"
  - "dépanner les composants"
  - "dépanner des contrôles"
  - "contrôles Windows Forms, débogage"
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# D&#233;pannage de la cr&#233;ation de contr&#244;les et de composants
Cette rubrique répertorie les problèmes courants suivants qui peuvent survenir lors du développement de composants et de contrôles.  Pour plus d'informations, consultez [Programming with Components](../Topic/Programming%20with%20Components.md).  
  
-   Impossible d'ajouter un contrôle à la boîte à outils  
  
-   Impossible de déboguer le composant ou contrôle utilisateur Windows Forms  
  
-   Un événement est déclenché deux fois dans un contrôle ou un composant hérité  
  
-   Erreur au moment du design : « Impossible de créer le composant '*Component Name*' »  
  
-   STAThreadAttribute  
  
-   L'icône du composant n'apparaît pas dans la boîte à outils  
  
## Impossible d'ajouter un contrôle à la boîte à outils  
 Si vous souhaitez ajouter à la **Boîte à outils** un contrôle personnalisé que vous avez créé dans un autre projet ou un contrôle tiers, vous devez le faire manuellement.  Si le projet actuel contient votre contrôle ou composant, il doit apparaître automatiquement dans la **Boîte à outils**.  Pour plus d'informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### Pour ajouter un contrôle à la boîte à outils  
  
1.  Cliquez avec le bouton droit sur la **Boîte à outils** et, dans le menu contextuel, sélectionnez **Choisir les éléments**.  
  
2.  Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, ajoutez le composant :  
  
    -   Si vous souhaitez ajouter un composant ou un contrôle .NET Framework, cliquez sur l'onglet **Composants .NET Framework**.  
  
         \- ou \-  
  
    -   Si vous souhaitez ajouter un composant COM ou un contrôle ActiveX, sélectionnez l'onglet **Composants COM**.  
  
3.  Si votre contrôle est répertorié dans la boîte de dialogue, assurez\-vous qu'il est sélectionné et cliquez sur **OK**.  
  
     Le contrôle est ajouté à la **Boîte à outils**.  
  
4.  Si votre contrôle n'est pas répertorié dans la boîte de dialogue, procédez de la façon suivante :  
  
    1.  Cliquez sur le bouton **Parcourir**.  
  
    2.  Accédez au dossier contenant le fichier .dll contenant votre contrôle.  
  
    3.  Sélectionnez le fichier .dll et cliquez sur **Ouvrir**.  
  
         Le contrôle apparaît dans la boîte de dialogue.  
  
    4.  Assurez\-vous que le contrôle est sélectionné, puis cliquez sur **OK**.  
  
         Le contrôle est ajouté à la **Boîte à outils**.  
  
## Impossible de déboguer le composant ou contrôle utilisateur Windows Forms  
 Si votre contrôle dérive de la classe <xref:System.Windows.Forms.UserControl>, vous pouvez déboguer son comportement à l'exécution avec le conteneur de test.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 D'autres composants et contrôles personnalisés ne sont pas des projets autonomes.  Ils doivent être hébergés par une application, telle qu'un projet Windows Forms.  Pour déboguer un contrôle ou un composant, vous devez l'ajouter à un projet Windows Forms.  
  
#### Pour déboguer un contrôle ou un composant  
  
1.  Dans le menu **Générer**, cliquez sur **Générer la solution** pour générer votre solution.  
  
2.  Dans le menu **Fichier**, cliquez sur **Ajouter**, puis sur **Nouveau projet** pour ajouter un projet test à votre application.  
  
3.  Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez **Application Windows** comme type de projet.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** du nouveau projet.  Dans le menu contextuel, cliquez sur **Ajouter une référence** pour ajouter une référence au projet qui contient le contrôle ou composant.  
  
5.  Créez une instance de votre contrôle ou composant dans le projet test.  Si votre composant se trouve dans la **Boîte à outils**, vous pouvez le faire glisser sur la surface du concepteur, ou créer l'instance par programme comme l'illustre l'exemple de code suivant :  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Vous pouvez à présent déboguer normalement votre contrôle ou composant.  
  
 Pour plus d'informations sur le débogage, consultez [Débogage dans Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md) et [Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## Un événement est déclenché deux fois dans un contrôle ou un composant hérité  
 Cela est probablement dû à une clause `Handles` dupliquée.  Pour plus d'informations, consultez [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md).  
  
## Erreur au moment du design : « Impossible de créer le composant 'Component Name' »  
 Votre composant ou contrôle doit fournir un constructeur par défaut sans paramètres.  Lorsque l'environnement de design crée une instance de votre composant ou contrôle, il n'essaie pas de fournir des paramètres aux surcharges de constructeur qui prennent des paramètres.  
  
## STAThreadAttribute  
 Le <xref:System.STAThreadAttribute> informe le common language runtime \(CLR\) que Windows Forms utilise le thread cloisonné \(STA, Single\-Threaded Apartment\).  Vous pouvez remarquer le comportement involontaire si vous n'appliquez pas cet attribut à la méthode `Main` de votre application Windows Forms.  Par exemple, les images d'arrière\-plan ne peuvent pas apparaître pour les contrôles comme <xref:System.Windows.Forms.ListView>.  Certains contrôles peuvent également requérir cet attribut pour un comportement correct dans les opérations de saisie semi\-automatique et glisser\-déplacer.  
  
## L'icône du composant n'apparaît pas dans la boîte à outils  
 Lorsque vous utilisez <xref:System.Drawing.ToolboxBitmapAttribute> pour associer une icône à votre composant personnalisé, la bitmap n'apparaît pas dans la Boîte à outils des composants générés automatiquement.  Pour afficher la bitmap, rechargez le contrôle à l'aide de la boîte de dialogue **Choisir des éléments de boîte à outils**.  Pour plus d'informations, consultez [Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## Voir aussi  
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)   
 [Component Authoring](../Topic/Component%20Authoring.md)   
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [Programming with Components](../Topic/Programming%20with%20Components.md)