---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le composite &#224; l&#39;aide de Visual&#160;Basic | Microsoft Docs"
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
  - "contrôles composites, créer"
  - "contrôles (Windows Forms), contrôles composites"
  - "contrôles personnalisés (Visual Basic)"
  - "contrôles personnalisés (Windows Forms), créer"
  - "contrôles utilisateur (Visual Basic)"
  - "contrôles utilisateur (Windows Forms), créer avec Visual Basic"
  - "UserControl (classe), procédures pas à pas"
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le composite &#224; l&#39;aide de Visual&#160;Basic
Les contrôles composites offrent le moyen de créer et de réutiliser des interfaces graphiques personnalisées.  Un contrôle composite est pour l'essentiel un composant doté d'une représentation visuelle.  Il peut être constitué d'un ou de plusieurs contrôles Windows Forms, de composants ou de blocs de code, lesquels peuvent développer des fonctionnalités en validant des entrées de l'utilisateur, en modifiant des propriétés d'affichage ou en effectuant d'autres tâches imposées par le créateur du contrôle.  Les contrôles composites peuvent être placés dans les Windows Forms de la même façon que les autres contrôles.  Dans la première partie de cette procédure pas à pas, créez un simple contrôle composite appelé `ctlClock`.  Dans la deuxième partie de la procédure, développez la fonctionnalité de `ctlClock` par l'intermédiaire de l'héritage.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 Lorsque vous créez un projet, vous spécifiez son nom pour définir l'espace de noms racine, le nom de l'assembly ainsi que celui du projet pour avoir la garantie que le composant par défaut sera placé dans l'espace de noms adéquat.  
  
#### Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
2.  Dans la liste de projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], sélectionnez le modèle de projet **Bibliothèque de contrôles Windows**, tapez `ctlClockLib` dans la zone **Nom**, puis cliquez sur **OK**.  
  
     Le nom de projet, `ctlClockLib`, est également assigné à l'espace de noms racine par défaut.  L'espace de noms racine sert à qualifier le nom des composants de l'assembly.  Par exemple, si deux assemblys contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l'aide de `ctlClockLib.ctlClock.`  
  
3.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **UserControl1.vb**, puis cliquez sur **Renommer**.  Remplacez le nom de fichier par `ctlClock.vb`.  Cliquez sur le bouton **Oui** à la question de savoir si vous souhaitez renommer toutes les références à l'élément de code "UserControl1".  
  
    > [!NOTE]
    >  Par défaut, un contrôle composite hérite de la classe <xref:System.Windows.Forms.UserControl> fournie par le système.  La classe <xref:System.Windows.Forms.UserControl> fournit les fonctionnalités requises par les contrôles composites et implémente des méthodes et des propriétés standard.  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.  
  
## Ajout de contrôles Windows et de composants au contrôle composite  
 L'interface visuelle est une partie essentielle de votre contrôle composite.  Elle est implémentée par l'ajout d'un ou de plusieurs contrôles Windows à l'aire du concepteur.  Dans la démonstration suivante, vous allez incorporer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter ses fonctionnalités.  
  
#### Pour ajouter un contrôle Label et un contrôle Timer à votre contrôle composite  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Concepteur de vues**.  
  
2.  Dans la Boîte à outils, développez le nœud **Contrôles communs**, puis double\-cliquez sur **Étiquette**.  
  
     Un contrôle  <xref:System.Windows.Forms.Label> nommé `Label1` est ajouté à votre contrôle sur l'aire du concepteur.  
  
3.  Dans le concepteur, cliquez sur **Label1**.  Dans la fenêtre Propriétés, définissez les propriétés suivantes.  
  
    |Propriété|Remplacez par|  
    |---------------|-------------------|  
    |**Nom**|`lblDisplay`|  
    |**Texte**|`(espace)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  Dans la **boîte à outils**, développez le nœud **Composants**, puis double\-cliquez sur **Minuterie**.  
  
     Une <xref:System.Windows.Forms.Timer> étant un composant, elle n'a pas de représentation visuelle au moment de l'exécution.  Par conséquent, ce composant n'apparaît pas avec les contrôles sur l'aire du concepteur, mais plutôt dans le Concepteur de composants \(sous forme de barre d'état au bas de l'aire du concepteur\).  
  
5.  Dans le Concepteur de composants, cliquez sur **Timer1**, puis attribuez à la propriété <xref:System.Windows.Forms.Timer.Interval%2A> la valeur `1000` et à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la valeur `True`.  
  
     La propriété <xref:System.Windows.Forms.Timer.Interval%2A> détermine la fréquence des graduations du composant Timer.  À chaque graduation, le composant `Timer1` exécute le code de l'événement `Timer1_Tick`.  L'intervalle représente le nombre de millisecondes entre deux graduations.  
  
6.  Dans le Concepteur de composants, double\-cliquez sur **Timer1** afin d'accéder à l'événement `Timer1_Tick` de `ctlClock`.  
  
7.  Modifiez le code afin qu'il ressemble au code ci\-après.  N'oubliez pas de remplacer le modificateur d'accès `Private` par `Protected`.  
  
     \[Visual Basic\]  
  
    ```  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     Ce code provoque l'affichage de l'heure actuelle dans `lblDisplay`.  Comme l'intervalle de `Timer1` a été fixé à `1 000`, cet événement se produit toutes les mille millisecondes, mettant ainsi à jour l'heure actuelle toutes les secondes.  
  
8.  Modifiez la méthode de telle manière qu'elle puisse être substituée.  Pour plus d'informations, consultez la section « Héritage d'un contrôle utilisateur » ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.  
  
## Ajout de propriétés au contrôle composite  
 Le contrôle horloge intègre à présent un contrôle <xref:System.Windows.Forms.Label> et un composant <xref:System.Windows.Forms.Timer>, avec chacun leur propre jeu de propriétés inhérentes.  Bien que les propriétés individuelles de ces contrôles ne seront pas accessibles pour les autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés.  Dans la procédure suivante, vous ajouterez à votre contrôle des propriétés permettant à l'utilisateur de changer la couleur d'arrière\-plan et le texte.  
  
#### Pour ajouter une propriété à votre contrôle composite  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Afficher le code**.  
  
     Vous voyez s'ouvrir l'éditeur de code de votre contrôle.  
  
2.  Recherchez l'instruction `Public Class ctlClock`.  Sous cette ligne, tapez le code ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous êtes sur le point de créer.  
  
3.  Insérez le code suivant sous les déclarations de variable de l'étape 2.  
  
     \[Visual Basic\]  
  
    ```  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     Le code précédent met deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, à la disposition des futurs utilisateurs du contrôle en appelant l'instruction `Property`.  Les instructions `Get` et `Set` assurent le stockage et la récupération de la valeur de propriété ainsi que du code permettant d'implémenter les fonctionnalités appropriées à la propriété.  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.  
  
## Test du contrôle  
 Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.  Testez le comportement à l'exécution de votre contrôle et essayez ses propriétés avec le **conteneur de test UserControl**.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### Pour tester le contrôle  
  
1.  Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.  
  
2.  Dans la grille des propriétés du conteneur de test, sélectionnez la propriété `ClockBackColor`, puis cliquez sur la flèche de déroulement pour afficher la palette de couleurs.  
  
3.  Choisissez une couleur en cliquant dessus.  
  
     La couleur d'arrière\-plan du contrôle est remplacée par celle que vous avez sélectionnée.  
  
4.  Utilisez une séquence d'événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.  
  
5.  Cliquez sur **Fermer** pour fermer le **conteneur de test UserControl**.  
  
     Dans cette section et les sections précédentes, vous avez vu comment les composants et les contrôles Windows pouvaient être associés à du code et à un empaquetage afin d'offrir des fonctionnalités personnalisées sous la forme d'un contrôle composite.  Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester ce dernier, une fois terminé.  Dans la section suivante, vous allez apprendre à construire un contrôle composite hérité en utilisant `ctlClock` comme base.  
  
## Héritage d'un contrôle composite  
 Dans les sections précédentes, vous avez appris à associer des contrôles Windows, des composants et du code dans des contrôles composites réutilisables.  Votre contrôle composite peut à présent être utilisé comme base pour construire d'autres contrôles.  Le processus par l'intermédiaire duquel une classe est dérivée d'une classe de base est appelé *héritage*.  Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`.  Ce contrôle sera dérivé de son contrôle parent, à savoir `ctlClock`.  Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en substituant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.  
  
 La première étape de la création d'un contrôle hérité consiste à le dériver de son parent.  Cette action crée un nouveau contrôle qui présente toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également servir de base pour l'ajout de fonctionnalités nouvelles ou modifiées.  
  
#### Pour créer le contrôle hérité  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, pointez sur **Ajouter**, puis cliquez sur **Contrôle utilisateur**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'ouvre.  
  
2.  Sélectionnez le modèle **Contrôle utilisateur hérité**.  
  
3.  Dans la zone **Nom**, tapez `ctlAlarmClock.vb`, puis cliquez sur **Ajouter**.  
  
     La boîte de dialogue **Sélecteur d'héritage** apparaît.  
  
4.  Sous **Nom du composant**, double\-cliquez sur **ctlClock**.  
  
5.  Dans l'Explorateur de solutions, parcourez les projets en cours.  
  
    > [!NOTE]
    >  Un fichier appelé **ctlAlarmClock.vb** a été ajouté au projet actuel.  
  
### Ajout de propriétés d'alarme  
 Vous ajoutez des propriétés à un contrôle hérité de la même façon qu'à un contrôle composite.  Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la valeur de date et d'heure à laquelle l'alarme se déclenche et `AlarmSet`, qui indique si l'alarme est activée ou non.  
  
##### Pour ajouter des propriétés à votre contrôle composite  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Afficher le code**.  
  
2.  Recherchez la déclaration de classe du contrôle ctlAlarmClock qui apparaît sous la forme `Public Class ctlAlarmClock`.  Dans la déclaration de classe, insérez le code ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### Ajout d'éléments à l'interface graphique du contrôle  
 Votre contrôle hérité présente une interface visuelle identique à celle du contrôle hérité.  Il possède les mêmes contrôles constituants que le contrôle parent, mais les propriétés de ces contrôles ne sont pas disponibles s'ils n'ont pas été exposés de manière spécifique.  Vous pouvez ajouter des éléments à l'interface graphique d'un contrôle composite hérité comme vous le feriez pour n'importe quel contrôle composite.  Pour modifier l'interface visuelle de votre alarme, vous allez ajouter un contrôle de type étiquette qui clignotera lors du déclenchement de l'alarme.  
  
##### Pour ajouter le contrôle Label  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Concepteur de vues**.  
  
     Le Concepteur de `ctlAlarmClock` s'ouvre dans la fenêtre principale.  
  
2.  Cliquez sur `lblDisplay` \(la partie affichage du contrôle\) et visualisez la fenêtre Propriétés.  
  
    > [!NOTE]
    >  Toutes les propriétés sont affichées, mais grisées.  Cela signifie que ces propriétés sont propres à `lblDisplay` et qu'elles ne peuvent pas être modifiées dans la fenêtre Propriétés.  Par défaut, les contrôles contenus dans un contrôle composite sont de type `Private` et leurs propriétés ne sont accessibles par aucun moyen.  
  
    > [!NOTE]
    >  Si vous voulez permettre aux futurs utilisateurs de votre contrôle utilisateur d'accéder à ses contrôles internes, déclarez ceux\-ci comme `Public` ou `Protected`.  Cela vous permettra de définir et de modifier à l'aide du code approprié les propriétés des contrôles contenus dans le contrôle composite.  
  
3.  Ajoutez un contrôle <xref:System.Windows.Forms.Label> à votre contrôle composite.  
  
4.  À l'aide de la souris, placez le contrôle <xref:System.Windows.Forms.Label> immédiatement sous la zone d'affichage.  Dans la fenêtre Propriétés, définissez les propriétés suivantes.  
  
    |Propriété|Paramètre|  
    |---------------|---------------|  
    |**Nom**|`lblAlarm`|  
    |**Texte**|Alarme \!|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`False`|  
  
### Ajout de la fonctionnalité d'alarme  
 Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle activant des fonctionnalités d'alarme dans votre contrôle composite.  Dans cette procédure, vous ajouterez du code pour comparer l'heure actuelle avec celle de l'alarme et, si les heures sont identiques, déclencher une alarme à la fois sonore et clignotante.  En substituant la méthode `Timer1_Tick` de `ctlClock` et en lui ajoutant le code supplémentaire, vous étendez la fonction de `ctlAlarmClock` tout en conservant toutes les fonctionnalités inhérentes de `ctlClock`.  
  
##### Pour substituer la méthode Timer1\_Tick de ctlClock  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Afficher le code**.  
  
2.  Recherchez l'instruction `Private blnAlarmSet As Boolean`.  Immédiatement sous cette instruction, tapez l'instruction ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  Recherchez l'instruction `End Class` en bas de la page.  Juste avant l'instruction `End Class`, ajoutez le code ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     L'ajout de ce code permet d'effectuer plusieurs tâches.  L'instruction `Overrides` ordonne au contrôle d'utiliser cette méthode à la place de celle qui a été héritée du contrôle de base.  Lorsqu'elle est appelée, cette méthode appelle la méthode à laquelle elle se substitue en appelant l'instruction `MyBase.Timer1_Tick`, ce qui garantit que toutes les fonctionnalités incorporées au contrôle d'origine sont reproduites dans ce contrôle.  Elle exécute ensuite du code supplémentaire afin d'intégrer la fonctionnalité d'alarme.  Un contrôle Label clignotant apparaît lorsque l'alarme se produit et un signal sonore se fait entendre.  
  
    > [!NOTE]
    >  Du moment que vous substituez un gestionnaire d'événements hérité, vous n'êtes pas tenu de spécifier l'événement à l'aide du mot clé `Handles`.  L'événement est déjà raccordé.  Vous substituez en fait seulement l'implémentation du gestionnaire.  
  
     Le contrôle de l'alarme est quasiment terminé.  Il ne reste plus qu'à implémenter un moyen de le désactiver.  Pour réaliser cette opération, vous ajouterez le code à la méthode `lblAlarm_Click`.  
  
##### Pour implémenter la méthode shutoff  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Concepteur de vues**.  
  
2.  Dans le concepteur, double\-cliquez sur **lblAlarm**.  L'**éditeur de code** s'ouvre à la ligne `Private Sub lblAlarm_Click`.  
  
3.  Modifiez cette méthode afin qu'elle ressemble au code ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.  
  
### Utilisation du contrôle hérité sur un formulaire  
 Vous pouvez tester votre contrôle hérité de la même façon que vous avez testé le contrôle de classe de base, `ctlClock` : appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Pour mettre votre contrôle en application, vous devrez l'héberger sur un formulaire.  Comme dans le cas d'un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de façon autonome et doit être hébergé dans un formulaire ou autre conteneur.  Comme `ctlAlarmClock` présente une plus grande profondeur de fonctionnalités, un code supplémentaire est requis pour tester ce contrôle.  Dans cette section, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`.  Vous allez écrire le code permettant de définir et d'afficher la propriété `AlarmTime` du contrôle `ctlAlarmClock`, puis tester ses fonctions inhérentes.  
  
##### Pour générer et ajouter votre contrôle à un formulaire de test  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, puis cliquez sur **Générer**.  
  
2.  Dans le menu **Fichier**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
3.  Ajoutez un nouveau projet d'**application Windows** à la solution et nommez\-le `Test`.  
  
     Le projet **Test** est ajouté à l'Explorateur de solutions.  
  
4.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nœud de projet `Test`, puis cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.  
  
5.  Cliquez sur l'onglet **Projets**.  Le projet **ctlClockLib** est répertorié sous **Nom du projet**.  Double\-cliquez sur **ctlClockLib** pour ajouter la référence au projet de test.  
  
6.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Générer**.  
  
7.  Dans la **Boîte à outils**, développez le nœud **Composants ctlClockLib**.  
  
8.  Double\-cliquez sur **ctlAlarmClock** pour ajouter une instance de `ctlAlarmClock` à votre formulaire.  
  
9. Dans la **Boîte à outils**, localisez **DateTimePicker** et double\-cliquez dessus afin d'ajouter un contrôle <xref:System.Windows.Forms.DateTimePicker> à votre formulaire, puis ajoutez un contrôle <xref:System.Windows.Forms.Label> en double\-cliquant sur **Label**.  
  
10. À l'aide de la souris, placez les contrôles dans le formulaire à un endroit adéquat.  
  
11. Définissez les propriétés de ces contrôles de la manière suivante.  
  
    |Contrôle|Propriété|Valeur|  
    |--------------|---------------|------------|  
    |`label1`|**Texte**|`(espace)`|  
    ||**Nom**|`lblTest`|  
    |`dateTimePicker1`|**Nom**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat>|  
  
12. Dans le concepteur, double\-cliquez sur **dtpTest**.  
  
     L'**éditeur de code** s'ouvre sur `Private Sub dtpTest_ValueChanged`.  
  
13. Modifiez le code afin qu'il ressemble au code ci\-dessous.  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Définir comme projet de démarrage**.  
  
15. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
     Le programme de test démarre.  Notez que l'heure actuelle est mise à jour dans le contrôle `ctlAlarmClock` et que l'heure de démarrage est affichée dans le contrôle <xref:System.Windows.Forms.DateTimePicker>.  
  
16. Cliquez sur le contrôle <xref:System.Windows.Forms.DateTimePicker> dans lequel sont affichées les minutes de l'heure.  
  
17. À l'aide du clavier, définissez pour les minutes une valeur supérieure d'une minute à l'heure actuelle affichée dans `ctlAlarmClock`.  
  
     L'heure de définition de l'alarme apparaît dans `lblTest`.  Attendez que l'heure affichée atteigne l'heure définie pour l'alarme.  Lorsque l'heure affichée atteint celle à laquelle l'alarme est définie, le signal sonore se fait entendre et `lblAlarm` se met à clignoter.  
  
18. Désactivez l'alarme en cliquant sur `lblAlarm`.  Vous pouvez maintenant réinitialiser l'alarme.  
  
     Cette procédure pas à pas a illustré plusieurs concepts clés.  Vous avez appris à créer un contrôle composite en associant des contrôles et des composants dans un conteneur de contrôle composite.  Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code afin d'implémenter des fonctionnalités personnalisées.  Dans la dernière section, vous avez appris à étendre les fonctionnalités d'un contrôle composite donné par l'intermédiaire de l'héritage, ainsi qu'à modifier les fonctionnalités des méthodes hôtes en substituant ces méthodes.  
  
## Voir aussi  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [Comment : créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)