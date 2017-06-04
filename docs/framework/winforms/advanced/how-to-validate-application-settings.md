---
title: "Comment&#160;: valider des param&#232;tres d&#39;application | Microsoft Docs"
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
  - "paramètres d'application, valider"
  - "paramètres d'application, Windows Forms"
  - "valider les paramètres de l'application"
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: valider des param&#232;tres d&#39;application
Cette rubrique montre comment valider des paramètres d'application avant qu'ils ne soient rendus persistants.  
  
 Puisque les paramètres d'application sont fortement typés, vous savez que les utilisateurs ne peuvent pas assigner les données d'un type inexact à un paramètre donné.  Toutefois, un utilisateur peut essayer d'assigner une valeur à un paramètre en dehors des limites acceptables \(par exemple, en fournissant une date de naissance qui se situe dans le futur\).  <xref:System.Configuration.ApplicationSettingsBase>, la classe parente de toutes les classes de paramètres d'application, expose quatre événements permettant d'activer la vérification de ces limites.  La gestion de ces événements place la totalité de votre code de validation à un emplacement unique au lieu de le répartir dans le projet.  
  
 L'événement que vous utilisez dépend du moment où vous devez valider vos paramètres, comme décrit dans le tableau suivant.  
  
|Événement|Occurrence et utilisation|  
|---------------|-------------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Se produit après le chargement initial d'un groupe de propriétés de paramètres.<br /><br /> Utilisez cet événement pour valider des valeurs initiales pour le groupe de propriétés entier avant leur utilisation dans l'application.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Se produit avant que la valeur d'une propriété de paramètres ne soit modifiée.<br /><br /> Utilisez cet événement pour valider une propriété avant qu'elle ne soit modifiée.  Il peut fournir des commentaires immédiats aux utilisateurs sur leurs actions et leurs choix.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Se produit après que la valeur d'une propriété de paramètres est modifiée.<br /><br /> Utilisez cet événement pour valider une propriété après qu'elle a été modifiée.  Cet événement est rarement utilisé pour la validation, à moins qu'une validation longue et asynchrone ne soit requise.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Se produit avant que le groupe de propriétés de paramètres ne soit stocké.<br /><br /> Utilisez cet événement pour valider des valeurs pour le groupe de propriétés entier avant qu'elles ne soient rendues persistantes sur disque.|  
  
 En général, vous n'utiliserez pas tous ces événements dans la même application à des fins de validation.  Par exemple, il est souvent possible de respecter toutes les conditions de validation requises en gérant uniquement l'événement <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>.  
  
 Un gestionnaire d'événements exécute généralement l'une des actions suivantes lorsqu'il détecte une valeur non valide :  
  
-   Fournit automatiquement une valeur correcte \(valeur par défaut, par exemple\).  
  
-   Interroge à nouveau l'utilisateur de code serveur pour obtenir des informations.  
  
-   Pour les événements déclenchés avant leurs actions associées, tels que <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> et <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, utilisez l'argument <xref:System.ComponentModel.CancelEventArgs> pour annuler l'opération.  
  
 Pour plus d'informations sur la gestion des événements, consultez [Vue d'ensemble des gestionnaires d'événements](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Les procédures suivantes indiquent comment tester une date de naissance valide à l'aide de l'événement <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ou <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>.  Ces procédures ont été écrites en supposant que vous avez déjà créé vos paramètres d'application ; dans cet exemple, nous exécuterons la vérification de limites sur un paramètre nommé  `DateOfBirth`.  Pour plus d'informations sur la création de paramètres, consultez [Comment : créer des paramètres d'application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### Pour obtenir l'objet de paramètres d'application  
  
-   Recherchez une référence à l'objet de paramètres d'application \(instance de wrapper\) en exécutant l'un des éléments à puce suivants :  
  
    -   Si vous avez créé vos paramètres à l'aide de la boîte de dialogue Paramètres de l'application de Visual Studio dans l'**éditeur de propriétés**, vous pouvez récupérer l'objet de paramètres par défaut généré pour votre langage via l'expression suivante.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         ou  
  
    -   Si vous êtes développeur Visual Basic et que vous avez créé vos paramètres d'application à l'aide du Concepteur de projets, vous pouvez récupérer vos paramètres en utilisant l'[My.Settings, objet](../../../../ocs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         ou  
  
    -   Si vous avez créé vos paramètres en dérivant directement de <xref:System.Configuration.ApplicationSettingsBase>, vous devez instancier votre classe manuellement.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Les procédures suivantes ont été écrites en supposant que l'objet de paramètres d'application a été obtenu en exécutant le dernier élément à puce de cette procédure.  
  
### Pour valider les paramètres de l'application lorsqu'un paramètre est modifié  
  
1.  Si vous êtes développeur C\#, ajoutez un gestionnaire d'événements pour l'événement <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> à l'événement  `Load`  de formulaire ou de contrôle.  
  
     ou  
  
     Si vous êtes développeur Visual Basic, vous devez déclarer la variable `Settings` à l'aide du mot clé `WithEvents`.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  Définissez le gestionnaire d'événements et écrivez le code dans ce gestionnaire pour exécuter la vérification de limites au niveau de la date de naissance.  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### Pour valider les paramètres de l'application au moment d'un enregistrement  
  
1.  Dans l'événement  `Load`  de votre formulaire ou de votre contrôle, ajoutez un gestionnaire d'événements pour l'événement <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  Définissez le gestionnaire d'événements et écrivez le code dans ce gestionnaire pour exécuter la vérification de limites au niveau de la date de naissance.  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [Comment : créer des paramètres d'application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)