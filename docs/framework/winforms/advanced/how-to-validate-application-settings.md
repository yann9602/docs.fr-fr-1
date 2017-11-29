---
title: "Comment : valider des paramètres d'application"
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
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 309429c2481bad3a8dff4708d9e2ea8a03057a4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="857c0-102">Comment : valider des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="857c0-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="857c0-103">Cette rubrique illustre la validation des paramètres d’application avant qu’ils ne soient rendus persistants.</span><span class="sxs-lookup"><span data-stu-id="857c0-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="857c0-104">Les paramètres d’application fortement typés empêchent les utilisateurs d’affecter les données d’un type incorrect pour un paramètre donné.</span><span class="sxs-lookup"><span data-stu-id="857c0-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="857c0-105">Toutefois, un utilisateur peut essayer d’assigner une valeur à un paramètre qui se situe en dehors des limites acceptables, par exemple en fournissant une date de naissance future.</span><span class="sxs-lookup"><span data-stu-id="857c0-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="857c0-106"><xref:System.Configuration.ApplicationSettingsBase>, la classe parente de toutes les classes de paramètres d’application, expose quatre événements pour activer la vérification de ces limites.</span><span class="sxs-lookup"><span data-stu-id="857c0-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="857c0-107">La gestion de ces événements place la totalité de votre code de validation dans un emplacement unique, plutôt que de le répartir dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="857c0-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="857c0-108">L’événement que vous utilisez dépend du moment où vous devez valider vos paramètres, comme décrit dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="857c0-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="857c0-109">Événement</span><span class="sxs-lookup"><span data-stu-id="857c0-109">Event</span></span>|<span data-ttu-id="857c0-110">Occurrence et utilisation</span><span class="sxs-lookup"><span data-stu-id="857c0-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="857c0-111">Se produit après le chargement initial d’un groupe de propriétés de paramètres.</span><span class="sxs-lookup"><span data-stu-id="857c0-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="857c0-112">Utilisez cet événement pour valider les valeurs initiales de l’ensemble du groupe de propriétés avant de les utiliser dans l’application.</span><span class="sxs-lookup"><span data-stu-id="857c0-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="857c0-113">Se produit avant la modification de la valeur d’une propriété unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="857c0-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="857c0-114">Utilisez cet événement pour valider une propriété unique avant sa modification.</span><span class="sxs-lookup"><span data-stu-id="857c0-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="857c0-115">Il peut fournir des commentaires immédiats aux utilisateurs à propos de leurs actions et de leurs choix.</span><span class="sxs-lookup"><span data-stu-id="857c0-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="857c0-116">Se produit après la modification de la valeur d’une propriété unique de paramètres.</span><span class="sxs-lookup"><span data-stu-id="857c0-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="857c0-117">Utilisez cet événement pour valider une propriété unique après sa modification.</span><span class="sxs-lookup"><span data-stu-id="857c0-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="857c0-118">Cet événement est rarement utilisé pour la validation, sauf si un processus de validation long et asynchrone est requis.</span><span class="sxs-lookup"><span data-stu-id="857c0-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="857c0-119">Se produit avant que le groupe de propriétés de paramètres ne soit stocké.</span><span class="sxs-lookup"><span data-stu-id="857c0-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="857c0-120">Utilisez cet événement pour valider les valeurs de l’ensemble du groupe de propriétés avant qu’elles ne soient rendues persistantes sur le disque.</span><span class="sxs-lookup"><span data-stu-id="857c0-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="857c0-121">En règle générale, vous n’utiliserez pas tous ces événements dans la même application à des fins de validation.</span><span class="sxs-lookup"><span data-stu-id="857c0-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="857c0-122">Par exemple, il est souvent possible de répondre à toutes les exigences de validation en gérant uniquement le <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> événement.</span><span class="sxs-lookup"><span data-stu-id="857c0-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="857c0-123">Un gestionnaire d’événements exécute généralement l’une des actions suivantes lorsqu’il détecte une valeur non valide :</span><span class="sxs-lookup"><span data-stu-id="857c0-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="857c0-124">Fournit automatiquement une valeur correcte, par exemple la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="857c0-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="857c0-125">Interroge de nouveau l’utilisateur de code serveur pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="857c0-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="857c0-126">Pour les événements déclenchés avant leurs actions associées, telles que <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> et <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, utilise le <xref:System.ComponentModel.CancelEventArgs> argument pour annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="857c0-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="857c0-127">Pour plus d’informations sur la gestion des événements, consultez [Vue d’ensemble des gestionnaires d’événements](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="857c0-127">For more information about event handling, see [Event Handlers Overview](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="857c0-128">Les procédures suivantes indiquent comment tester une date de naissance valide à l’aide du <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ou <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> événement.</span><span class="sxs-lookup"><span data-stu-id="857c0-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="857c0-129">Ces procédures ont été écrites en supposant que vous avez déjà créé vos paramètres d’application. Dans cet exemple, nous vérifions les limites d’un paramètre nommé `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="857c0-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="857c0-130">Pour plus d’informations sur la création de paramètres, consultez [Comment : créer des paramètres d’application](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="857c0-130">For more information about creating settings, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="857c0-131">Pour obtenir l’objet des paramètres de l’application</span><span class="sxs-lookup"><span data-stu-id="857c0-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="857c0-132">Obtenez une référence à l’objet des paramètres d’application (instance de wrapper) en respectant l’un des éléments de la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="857c0-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="857c0-133">Si vous avez créé vos paramètres à l’aide de la boîte de dialogue Paramètres de l’application Visual Studio de l’**éditeur de propriétés**, vous pouvez récupérer l’objet de paramètres par défaut généré pour votre langage par le biais de l’expression suivante.</span><span class="sxs-lookup"><span data-stu-id="857c0-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="857c0-134">ou</span><span class="sxs-lookup"><span data-stu-id="857c0-134">-or-</span></span>  
  
    -   <span data-ttu-id="857c0-135">Si vous êtes un développeur Visual Basic et si vous avez créé vos paramètres d’application à l’aide du Concepteur de projet, vous pouvez récupérer vos paramètres à l’aide de l’[objet My.Settings](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="857c0-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="857c0-136">ou</span><span class="sxs-lookup"><span data-stu-id="857c0-136">-or-</span></span>  
  
    -   <span data-ttu-id="857c0-137">Si vous avez créé vos paramètres en dérivant de <xref:System.Configuration.ApplicationSettingsBase> directement, vous devez instancier votre classe manuellement.</span><span class="sxs-lookup"><span data-stu-id="857c0-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="857c0-138">Les procédures suivantes ont été écrites en supposant que l’objet des paramètres d’application a été obtenu par le biais du dernier élément répertorié dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="857c0-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="857c0-139">Pour valider les paramètres de l’application lors de la modification d’un paramètre</span><span class="sxs-lookup"><span data-stu-id="857c0-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="857c0-140">Si vous êtes un développeur c#, dans votre formulaire ou de contrôle `Load` événement, ajoutez un gestionnaire d’événements pour le <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> événement.</span><span class="sxs-lookup"><span data-stu-id="857c0-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="857c0-141">ou</span><span class="sxs-lookup"><span data-stu-id="857c0-141">-or-</span></span>  
  
     <span data-ttu-id="857c0-142">Si vous êtes un développeur Visual Basic, vous devez déclarer la variable `Settings` à l’aide du mot clé`WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="857c0-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
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
  
2.  <span data-ttu-id="857c0-143">Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.</span><span class="sxs-lookup"><span data-stu-id="857c0-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="857c0-144">Pour valider les paramètres d’application en cas d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="857c0-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="857c0-145">Dans votre formulaire ou de contrôle `Load` événement, ajoutez un gestionnaire d’événements pour le <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> événement.</span><span class="sxs-lookup"><span data-stu-id="857c0-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
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
  
2.  <span data-ttu-id="857c0-146">Définissez le gestionnaire d’événements et insérez-y le code pour vérifier les limites de la date de naissance.</span><span class="sxs-lookup"><span data-stu-id="857c0-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="857c0-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="857c0-147">See Also</span></span>  
 [<span data-ttu-id="857c0-148">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="857c0-148">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="857c0-149">Comment : créer des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="857c0-149">How to: Create Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
