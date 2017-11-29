---
title: "Comment : créer des paramètres d'application"
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
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="375bb-102">Comment : créer des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="375bb-102">How to: Create Application Settings</span></span>
<span data-ttu-id="375bb-103">À l'aide de code managé, vous pouvez créer des paramètres d'application et les lier à des propriétés ou des contrôles sur votre formulaire, pour que ces paramètres soient chargés et enregistrés automatiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="375bb-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="375bb-104">Dans la procédure suivante, vous allez créer manuellement une classe wrapper qui dérive de <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="375bb-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="375bb-105">Vous ajouterez à cette classe une propriété accessible publiquement pour chaque paramètre d'application que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="375bb-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="375bb-106">Vous pouvez également appliquer cette procédure avec un minimum de code dans le concepteur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="375bb-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="375bb-107">Consultez également [Comment : créer des Application paramètres de l’aide du concepteur](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="375bb-107">Also see [How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="375bb-108">Pour créer des paramètres d'application par programmation</span><span class="sxs-lookup"><span data-stu-id="375bb-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="375bb-109">Ajoutez une nouvelle classe à votre projet et renommez-la.</span><span class="sxs-lookup"><span data-stu-id="375bb-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="375bb-110">Pour cette procédure, nous appellerons cette classe `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="375bb-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="375bb-111">Modifiez la définition de la classe pour qu'elle dérive de <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="375bb-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="375bb-112">Définissez une propriété sur cette classe wrapper pour chaque paramètre d'application nécessaire et appliquez cette propriété avec le <xref:System.Configuration.ApplicationScopedSettingAttribute> ou le <xref:System.Configuration.UserScopedSettingAttribute>, selon la portée du paramètre.</span><span class="sxs-lookup"><span data-stu-id="375bb-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="375bb-113">Pour plus d’informations sur la portée des paramètres, consultez [vue d’ensemble des paramètres d’Application](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="375bb-113">For more information about settings scope, see [Application Settings Overview](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span> <span data-ttu-id="375bb-114">Votre code doit maintenant ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="375bb-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="375bb-115">Créez une instance de cette classe wrapper dans votre application.</span><span class="sxs-lookup"><span data-stu-id="375bb-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="375bb-116">Il s'agira généralement d'un membre privé du formulaire principal.</span><span class="sxs-lookup"><span data-stu-id="375bb-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="375bb-117">Maintenant que vous avez défini votre classe, vous devez la lier à une propriété. Ici, il s'agit de la propriété <xref:System.Windows.Forms.Form.BackColor%2A> de votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="375bb-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="375bb-118">Vous pouvez le faire dans votre formulaire `Load` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="375bb-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="375bb-119">Si vous proposez une manière de modifier les paramètres au moment de l'exécution, vous devrez enregistrer les paramètres actuels de l'utilisateur sur disque lors de la fermeture de votre formulaire, sinon ces modifications seront perdues.</span><span class="sxs-lookup"><span data-stu-id="375bb-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="375bb-120">Vous avez créé un paramètre d'application et vous l'avez lié à la propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="375bb-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="375bb-121">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="375bb-121">.NET Framework Security</span></span>  
 <span data-ttu-id="375bb-122">Le fournisseur de paramètres par défaut, <xref:System.Configuration.LocalFileSettingsProvider>, conserve les informations dans des fichiers de configuration en texte brut.</span><span class="sxs-lookup"><span data-stu-id="375bb-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="375bb-123">Cela limite la sécurité à la sécurité d'accès de fichier fournie par le système d'exploitation pour l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="375bb-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="375bb-124">Pour cette raison, vous devez faire attention aux informations stockées dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="375bb-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="375bb-125">Par exemple, l'une des utilisations courantes des paramètres d'application consiste à stocker des chaînes de connexion qui pointent vers le magasin de données de l'application.</span><span class="sxs-lookup"><span data-stu-id="375bb-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="375bb-126">Toutefois, pour des raisons de sécurité, ces chaînes ne doivent pas inclure de mots de passe.</span><span class="sxs-lookup"><span data-stu-id="375bb-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="375bb-127">Pour plus d'informations sur les chaînes de connexion, consultez <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="375bb-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375bb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="375bb-128">See Also</span></span>  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [<span data-ttu-id="375bb-129">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="375bb-129">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="375bb-130">Guide pratique pour valider des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="375bb-130">How to: Validate Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
