---
title: "Création d’écouteurs de journalisation personnalisés (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc6fde8dcbb27157f3fd180ad393bb406222195e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="c06c6-102">Procédure pas à pas : création d'écouteurs de journalisation personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c06c6-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="c06c6-103">Cette procédure pas à pas illustre comment créer un écouteur de journalisation personnalisé et le configurer pour écouter la sortie de l’objet `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="c06c6-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="c06c6-104">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c06c6-104">Getting Started</span></span>  
 <span data-ttu-id="c06c6-105">Les écouteurs de journalisation doivent hériter de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="c06c6-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="c06c6-106">Pour créer l’écouteur</span><span class="sxs-lookup"><span data-stu-id="c06c6-106">To create the listener</span></span>  
  
-   <span data-ttu-id="c06c6-107">Dans votre application, créez une classe nommée `SimpleListener` qui hérite de <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="c06c6-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     <span data-ttu-id="c06c6-108">[!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c06c6-108">[!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]</span></span>  
  
     <span data-ttu-id="c06c6-109">Les méthodes <xref:System.Diagnostics.TraceListener.Write%2A> et <xref:System.Diagnostics.TraceListener.WriteLine%2A>, requises par la classe de base, appellent `MsgBox` pour afficher leur entrée.</span><span class="sxs-lookup"><span data-stu-id="c06c6-109">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="c06c6-110">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> est appliqué aux méthodes <xref:System.Diagnostics.TraceListener.Write%2A> et <xref:System.Diagnostics.TraceListener.WriteLine%2A> afin que leurs attributs correspondent aux méthodes de classe de base.</span><span class="sxs-lookup"><span data-stu-id="c06c6-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="c06c6-111">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> permet à l’hôte qui exécute le code de déterminer que ce dernier expose la synchronisation de la protection de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c06c6-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c06c6-112">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> n’est effectif que sur les applications non managées, telles que SQL Server, qui hébergent le Common Language Runtime et implémentent la protection de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c06c6-112">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="c06c6-113">Pour vérifier que `My.Application.Log` utilise votre écouteur de journalisation, vous devez attribuer un nom fort à l’assembly qui le contient.</span><span class="sxs-lookup"><span data-stu-id="c06c6-113">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="c06c6-114">La procédure suivante fournit des étapes simples pour créer un assembly d’écouteur de journalisation portant un nom fort.</span><span class="sxs-lookup"><span data-stu-id="c06c6-114">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="c06c6-115">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617).</span><span class="sxs-lookup"><span data-stu-id="c06c6-115">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="c06c6-116">Pour attribuer un nom fort à l’assembly de l’écouteur de journalisation</span><span class="sxs-lookup"><span data-stu-id="c06c6-116">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="c06c6-117">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c06c6-118">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-118">On the **Project** menu, choose **Properties**.</span></span> <span data-ttu-id="c06c6-119">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="c06c6-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="c06c6-120">Cliquez sur l’onglet **Signature**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-120">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="c06c6-121">Sélectionnez la zone **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-121">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="c06c6-122">Sélectionnez **\<Nouveau** dans la liste déroulante **Choisir un fichier de clé de nom fort**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-122">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="c06c6-123">La boîte de dialogue **Créer une clé de nom fort** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="c06c6-123">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="c06c6-124">Fournissez un nom pour le fichier de clé dans la zone **Nom du fichier de clé**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-124">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="c06c6-125">Entrez un mot de passe dans les zones **Entrer le mot de passe** et **Confirmer le mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-125">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="c06c6-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-126">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="c06c6-127">Régénérez l’application.</span><span class="sxs-lookup"><span data-stu-id="c06c6-127">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="c06c6-128">Ajout de l’écouteur</span><span class="sxs-lookup"><span data-stu-id="c06c6-128">Adding the Listener</span></span>  
 <span data-ttu-id="c06c6-129">Maintenant que l’assembly a un nom fort, vous devez déterminer le nom fort de l’écouteur afin que `My.Application.Log` utilise votre écouteur de journalisation.</span><span class="sxs-lookup"><span data-stu-id="c06c6-129">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="c06c6-130">Le format d’un type portant un nom fort se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="c06c6-130">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="c06c6-131">\<nom type>, \<nom assembly>, \<numéro version>, \<culture>, \<nom fort></span><span class="sxs-lookup"><span data-stu-id="c06c6-131">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="c06c6-132">Pour déterminer le nom fort de l’écouteur</span><span class="sxs-lookup"><span data-stu-id="c06c6-132">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="c06c6-133">Le code suivant indique comment déterminer le nom de type fort pour `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="c06c6-133">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     <span data-ttu-id="c06c6-134">[!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c06c6-134">[!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]</span></span>  
  
     <span data-ttu-id="c06c6-135">Le nom fort du type dépend de votre projet.</span><span class="sxs-lookup"><span data-stu-id="c06c6-135">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="c06c6-136">Avec le nom fort, vous pouvez ajouter l’écouteur à la collection de l’écouteur de journalisation `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="c06c6-136">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="c06c6-137">Pour ajouter l’écouteur à My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c06c6-137">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="c06c6-138">Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-138">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="c06c6-139">ou</span><span class="sxs-lookup"><span data-stu-id="c06c6-139">-or-</span></span>  
  
     <span data-ttu-id="c06c6-140">S’il existe un fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="c06c6-140">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="c06c6-141">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-141">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="c06c6-142">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-142">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="c06c6-143">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c06c6-143">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="c06c6-144">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », qui se trouve dans la section `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="c06c6-144">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="c06c6-145">La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="c06c6-145">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="c06c6-146">Ajoutez cet élément à la section `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="c06c6-146">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="c06c6-147">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="c06c6-147">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="c06c6-148">Ajoutez cet élément à cette section `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="c06c6-148">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="c06c6-149">Modifiez la valeur de `SimpleLogStrongName` pour qu’elle soit le nom fort de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="c06c6-149">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06c6-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c06c6-150">See Also</span></span>  
 <span data-ttu-id="c06c6-151"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c06c6-151"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="c06c6-152">[Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="c06c6-152">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="c06c6-153">[Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="c06c6-153">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="c06c6-154">[Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="c06c6-154">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 [<span data-ttu-id="c06c6-155">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c06c6-155">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

