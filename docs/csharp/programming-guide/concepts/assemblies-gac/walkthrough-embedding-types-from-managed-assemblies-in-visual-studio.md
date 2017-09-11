---
title: "Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7b003e76229a06883adc22f933f08663330f0c9d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="f1cab-102">Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="f1cab-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="f1cab-103">Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version.</span><span class="sxs-lookup"><span data-stu-id="f1cab-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="f1cab-104">Autrement dit, votre programme peut être écrit de façon à ce qu’il utilise des types de plusieurs versions d’une bibliothèque managée sans que vous n’ayez à effectuer de recompilation pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="f1cab-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="f1cab-105">L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f1cab-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="f1cab-106">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f1cab-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="f1cab-107">Toutefois, vous pouvez également utiliser l’incorporation de type avec une solution totalement managée.</span><span class="sxs-lookup"><span data-stu-id="f1cab-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="f1cab-108">Les informations de type peuvent être incorporées à partir d’un assembly doté des caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1cab-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="f1cab-109">L’assembly expose au moins une interface publique.</span><span class="sxs-lookup"><span data-stu-id="f1cab-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="f1cab-110">Les interfaces incorporées sont annotées avec un attribut `ComImport` et un attribut `Guid` (et un GUID unique).</span><span class="sxs-lookup"><span data-stu-id="f1cab-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="f1cab-111">L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f1cab-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="f1cab-112">(Par défaut, les modèles de projet Visual C# incluent un attribut `Guid` au niveau de l’assembly.)</span><span class="sxs-lookup"><span data-stu-id="f1cab-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="f1cab-113">Après avoir spécifié les interfaces publiques qui peuvent être incorporées, vous pouvez créer des classes runtime qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="f1cab-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="f1cab-114">Un programme client peut ensuite incorporer les informations de type pour ces interfaces au moment de la conception en référençant l’assembly qui contient les interfaces publiques et en affectant à la propriété `Embed Interop Types` de la référence la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="f1cab-115">Cela revient à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l’option de compilateur `/link`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="f1cab-116">Le programme client peut ensuite charger des instances de vos objets d’exécution possédant le même type que ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="f1cab-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="f1cab-117">Si vous créez une version de votre assembly runtime avec nom fort, le programme client n’a pas besoin d’être recompilé avec l’assembly runtime mis à jour.</span><span class="sxs-lookup"><span data-stu-id="f1cab-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="f1cab-118">En revanche, le programme client continue d’utiliser la version de l’assembly runtime disponible avec les informations de type incorporées pour les interfaces publiques.</span><span class="sxs-lookup"><span data-stu-id="f1cab-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="f1cab-119">Étant donné que la fonction principale de l’incorporation de type est de prendre en charge l’incorporation d’informations de type à partir d’assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution totalement managée :</span><span class="sxs-lookup"><span data-stu-id="f1cab-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="f1cab-120">Seuls les attributs spécifiques à COM Interop sont incorporés ; les autres attributs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="f1cab-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="f1cab-121">Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé au-delà de la limite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f1cab-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="f1cab-122">Les exemples de passage de la limite de l’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type à partir d’un type défini dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="f1cab-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="f1cab-123">Les constantes ne sont pas incorporées.</span><span class="sxs-lookup"><span data-stu-id="f1cab-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="f1cab-124">La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> ne prend pas en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="f1cab-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> class does not support an embedded type as a key.</span></span> <span data-ttu-id="f1cab-125">Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="f1cab-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="f1cab-126">Dans cette procédure pas à pas, vous exécuterez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1cab-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="f1cab-127">Créer un assembly avec nom fort doté d’une interface publique contenant des informations de type qui peuvent être incorporées.</span><span class="sxs-lookup"><span data-stu-id="f1cab-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="f1cab-128">Créer un assembly runtime avec nom fort qui implémente cette interface publique.</span><span class="sxs-lookup"><span data-stu-id="f1cab-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="f1cab-129">Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="f1cab-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="f1cab-130">Modifier et régénérer l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="f1cab-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="f1cab-131">Exécuter le programme client pour constater que la nouvelle version de l’assembly runtime est utilisée sans devoir recompiler le programme client.</span><span class="sxs-lookup"><span data-stu-id="f1cab-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="f1cab-132">Création d’une interface</span><span class="sxs-lookup"><span data-stu-id="f1cab-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="f1cab-133">Pour créer le projet d’interface d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="f1cab-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="f1cab-134">Dans Visual Studio, dans le menu **Fichier**, choisissez **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1cab-135">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f1cab-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1cab-136">Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="f1cab-137">Dans la zone **Nom**, tapez `TypeEquivalenceInterface`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="f1cab-138">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="f1cab-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1cab-139">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier Class1.cs, puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="f1cab-140">Renommez le fichier `ISampleInterface.cs` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="f1cab-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="f1cab-141">Quand vous renommez le fichier, la classe est également renommée `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="f1cab-142">Cette classe représente l’interface publique pour la classe.</span><span class="sxs-lookup"><span data-stu-id="f1cab-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="f1cab-143">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="f1cab-144">Cliquez sur l’onglet **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-144">Click the the **Build** tab.</span></span> <span data-ttu-id="f1cab-145">Affectez au chemin de sortie un emplacement valide sur votre ordinateur de développement, tel que `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-145">Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="f1cab-146">Cet emplacement sera également utilisé dans une étape ultérieure de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="f1cab-146">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="f1cab-147">Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-147">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="f1cab-148">Sélectionnez l’option **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-148">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="f1cab-149">Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-149">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="f1cab-150">Dans la zone **Nom du fichier de clé**, tapez `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-150">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="f1cab-151">Décochez la case **Protéger mon fichier de clé par un mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-151">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="f1cab-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-152">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f1cab-153">Ouvrez le fichier ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="f1cab-153">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="f1cab-154">Ajoutez le code suivant au fichier de classe ISampleInterface pour créer l’interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="f1cab-154">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
  
    namespace TypeEquivalenceInterface  
    {  
        [ComImport]  
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]  
        public interface ISampleInterface  
        {  
            void GetUserInput();  
            string UserInput { get; }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="f1cab-155">Dans le menu **Outils**, cliquez sur **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-155">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="f1cab-156">Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-156">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="f1cab-157">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-157">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="f1cab-158">Dans l’attribut `Guid`, supprimez l’exemple de GUID et collez le GUID que vous avez copié à partir de la boîte de dialogue **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-158">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="f1cab-159">Supprimez les accolades ({}) du GUID copié.</span><span class="sxs-lookup"><span data-stu-id="f1cab-159">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="f1cab-160">Dans l’**Explorateur de solutions**, développez le dossier **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-160">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="f1cab-161">Double-cliquez sur le fichier AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="f1cab-161">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="f1cab-162">Ajoutez l’attribut suivant au fichier.</span><span class="sxs-lookup"><span data-stu-id="f1cab-162">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="f1cab-163">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="f1cab-163">Save the file.</span></span>  
  
10. <span data-ttu-id="f1cab-164">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="f1cab-164">Save the project.</span></span>  
  
11. <span data-ttu-id="f1cab-165">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-165">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="f1cab-166">Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1cab-166">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="f1cab-167">Création d’une classe runtime</span><span class="sxs-lookup"><span data-stu-id="f1cab-167">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="f1cab-168">Pour créer le projet d’exécution d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="f1cab-168">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="f1cab-169">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-169">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1cab-170">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f1cab-170">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1cab-171">Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-171">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="f1cab-172">Dans la zone **Nom**, tapez `TypeEquivalenceRuntime`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-172">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="f1cab-173">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="f1cab-173">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1cab-174">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier Class1.cs, puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-174">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="f1cab-175">Renommez le fichier `SampleClass.cs` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="f1cab-175">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="f1cab-176">Quand vous renommez le fichier, la classe est également renommée `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-176">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="f1cab-177">Cette classe va implémenter l’interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-177">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="f1cab-178">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-178">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="f1cab-179">Cliquez sur l’onglet **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-179">Click the **Build** tab.</span></span> <span data-ttu-id="f1cab-180">Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-180">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="f1cab-181">Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-181">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="f1cab-182">Sélectionnez l’option **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-182">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="f1cab-183">Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-183">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="f1cab-184">Dans la zone **Nom du fichier de clé**, tapez `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-184">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="f1cab-185">Décochez la case **Protéger mon fichier de clé par un mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-185">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="f1cab-186">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-186">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f1cab-187">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-187">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="f1cab-188">Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1cab-188">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="f1cab-189">Sélectionnez le fichier TypeEquivalenceInterface.dll et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-189">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="f1cab-190">Dans l’**Explorateur de solutions**, développez le dossier **Références**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-190">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="f1cab-191">Sélectionnez la référence TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="f1cab-191">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="f1cab-192">Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Version spécifique** la valeur **False**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-192">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="f1cab-193">Ajoutez le code suivant au fichier de classe SampleClass pour créer la classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="f1cab-193">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
  
    namespace TypeEquivalenceRuntime  
    {  
        public class SampleClass : ISampleInterface  
        {  
            private string p_UserInput;  
            public string UserInput { get { return p_UserInput; } }  
  
            public void GetUserInput()  
            {  
                Console.WriteLine("Please enter a value:");  
                p_UserInput = Console.ReadLine();  
            }  
        }  
    )  
    ```  
  
9. <span data-ttu-id="f1cab-194">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="f1cab-194">Save the project.</span></span>  
  
10. <span data-ttu-id="f1cab-195">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-195">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="f1cab-196">Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1cab-196">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="f1cab-197">Création d’un projet client</span><span class="sxs-lookup"><span data-stu-id="f1cab-197">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="f1cab-198">Pour créer le projet client d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="f1cab-198">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="f1cab-199">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-199">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1cab-200">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f1cab-200">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1cab-201">Sélectionnez **Application console** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-201">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="f1cab-202">Dans la zone **Nom**, tapez `TypeEquivalenceClient`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-202">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="f1cab-203">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="f1cab-203">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1cab-204">Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-204">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="f1cab-205">Cliquez sur l’onglet **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-205">Click the **Build** tab.</span></span> <span data-ttu-id="f1cab-206">Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-206">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="f1cab-207">Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-207">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="f1cab-208">Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1cab-208">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="f1cab-209">Sélectionnez le fichier TypeEquivalenceInterface.dll (pas le fichier TypeEquivalenceRuntime.dll) et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-209">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="f1cab-210">Dans l’**Explorateur de solutions**, développez le dossier **Références**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-210">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="f1cab-211">Sélectionnez la référence TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="f1cab-211">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="f1cab-212">Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Incorporer les types d’interopérabilité** la valeur **True**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-212">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="f1cab-213">Ajoutez le code suivant au fichier Program.cs pour créer le programme client.</span><span class="sxs-lookup"><span data-stu-id="f1cab-213">Add the following code to the Program.cs file to create the client program.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
    using System.Reflection;  
  
    namespace TypeEquivalenceClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");  
                ISampleInterface sampleClass =   
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");  
                sampleClass.GetUserInput();  
                Console.WriteLine(sampleClass.UserInput);  
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());  
                Console.ReadLine();  
            }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="f1cab-214">Appuyez sur CTRL+F5 pour générer et exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="f1cab-214">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="f1cab-215">Modification de l’interface</span><span class="sxs-lookup"><span data-stu-id="f1cab-215">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="f1cab-216">Pour modifier l’interface</span><span class="sxs-lookup"><span data-stu-id="f1cab-216">To modify the interface</span></span>  
  
1.  <span data-ttu-id="f1cab-217">Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-217">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="f1cab-218">Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-218">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="f1cab-219">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="f1cab-219">Click the **Application** tab.</span></span> <span data-ttu-id="f1cab-220">Cliquez sur le bouton **Informations de l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-220">Click the **Assembly Information** button.</span></span> <span data-ttu-id="f1cab-221">Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-221">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="f1cab-222">Ouvrez le fichier SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="f1cab-222">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="f1cab-223">Ajoutez la ligne de code suivante à l’interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="f1cab-223">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="f1cab-224">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="f1cab-224">Save the file.</span></span>  
  
4.  <span data-ttu-id="f1cab-225">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="f1cab-225">Save the project.</span></span>  
  
5.  <span data-ttu-id="f1cab-226">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-226">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="f1cab-227">Une nouvelle version du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1cab-227">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="f1cab-228">Modification de la classe runtime</span><span class="sxs-lookup"><span data-stu-id="f1cab-228">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="f1cab-229">Pour modifier la classe runtime</span><span class="sxs-lookup"><span data-stu-id="f1cab-229">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="f1cab-230">Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-230">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="f1cab-231">Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-231">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="f1cab-232">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="f1cab-232">Click the **Application** tab.</span></span> <span data-ttu-id="f1cab-233">Cliquez sur le bouton **Informations de l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-233">Click the **Assembly Information** button.</span></span> <span data-ttu-id="f1cab-234">Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f1cab-234">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="f1cab-235">Ouvrez le fichier SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="f1cab-235">Open the SampleClass.cs file.</span></span> <span data-ttu-id="f1cab-236">Ajoutez les lignes de code suivantes à la classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="f1cab-236">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="f1cab-237">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="f1cab-237">Save the file.</span></span>  
  
4.  <span data-ttu-id="f1cab-238">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="f1cab-238">Save the project.</span></span>  
  
5.  <span data-ttu-id="f1cab-239">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f1cab-239">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="f1cab-240">Une version mise à jour du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération précédemment spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1cab-240">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="f1cab-241">Dans l’Explorateur de fichiers, ouvrez le dossier du chemin de sortie (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1cab-241">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="f1cab-242">Double-cliquez sur le fichier TypeEquivalenceClient.exe pour exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="f1cab-242">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="f1cab-243">Le programme reflète la nouvelle version de l’assembly TypeEquivalenceRuntime sans aucune recompilation.</span><span class="sxs-lookup"><span data-stu-id="f1cab-243">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cab-244">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1cab-244">See Also</span></span>  
 <span data-ttu-id="f1cab-245">[/link (Options du compilateur C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="f1cab-245">[/link (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md) </span></span>  
 <span data-ttu-id="f1cab-246">[Guide de programmation C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1cab-246">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f1cab-247">[Programmation à l’aide d’assemblys](../../../../framework/app-domains/programming-with-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f1cab-247">[Programming with Assemblies](../../../../framework/app-domains/programming-with-assemblies.md) </span></span>  
 [<span data-ttu-id="f1cab-248">Assemblys et le Global Assembly Cache (C#)</span><span class="sxs-lookup"><span data-stu-id="f1cab-248">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

