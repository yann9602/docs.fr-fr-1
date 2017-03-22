---
title: "Procédure pas à pas : Incorporation de Types provenant d’assemblys dans Visual Studio (Visual Basic) managé | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Procédure pas à pas : Incorporation de Types provenant d’assemblys managés dans Visual Studio (Visual Basic)
Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application à l’indépendance de version. Autrement dit, votre programme peut être écrit pour utiliser des types de plusieurs versions d’une bibliothèque managée sans devoir être recompilée pour chaque version.  
  
 L’incorporation de type est fréquemment utilisée avec COM interop, tel qu’une application qui utilise des objets automation de Microsoft Office. Incorporation d’informations de type permet à la même version d’un programme de fonctionner avec différentes versions de Microsoft Office sur des ordinateurs différents. Toutefois, vous pouvez également utiliser l’incorporation avec une solution entièrement gérée de type.  
  
 Les informations de type peuvent être incorporées à partir d’un assembly qui possède les caractéristiques suivantes :  
  
-   L’assembly expose au moins une interface publique.  
  
-   Les interfaces incorporées sont annotées avec un `ComImport` attribut et un `Guid` attribut (et un GUID unique).  
  
-   L’assembly est annoté avec le `ImportedFromTypeLib` attribut ou `PrimaryInteropAssembly` attribut et niveau assembly `Guid` attribut. (Par défaut, les modèles de projet Visual Basic incluent un niveau de l’assembly `Guid` attribut.)  
  
 Après avoir spécifié les interfaces publiques qui peuvent être intégrés, vous pouvez créer des classes d’exécution qui implémentent ces interfaces. Un programme client peut ensuite incorporer les informations de type pour ces interfaces au moment du design en référençant l’assembly qui contient les interfaces publiques et les `Embed Interop Types` propriétés de la référence à `True`. Cela est équivalent à l’aide du compilateur de ligne de commande et à référencer l’assembly à l’aide de la `/link` option du compilateur. Le programme client peut ensuite charger des instances de vos objets runtime typés en tant que ces interfaces. Si vous créez une nouvelle version de votre assembly de runtime avec nom fort, le programme client ne dispose pas d’être recompilé avec l’assembly de runtime mis à jour. Au lieu de cela, le programme client continue à utiliser quelle que soit la version de l’assembly de runtime est disponible, en utilisant les informations de type incorporées pour les interfaces publiques.  
  
 Étant donné que la fonction principale de l’incorporation de type est de prendre en charge l’incorporation des informations de type d’assemblys d’interopérabilité COM, les limitations suivantes s’appliquent lorsque vous incorporez des informations de type dans une solution entièrement gérée :  
  
-   Seuls les attributs spécifiques à COM interop sont incorporés ; les autres attributs sont ignorés.  
  
-   Si un type utilise des paramètres génériques et le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé au-delà des limites d’un assembly. Sont des exemples de dépasser la limite de l’assembly appelant une méthode à partir d’un autre assembly ou la dérivation d’un type d’un type défini dans un autre assembly.  
  
-   Les constantes ne sont pas incorporées.  
  
-   La <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>classe ne prend pas en charge un type incorporé en tant que clé.</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé en tant que clé.  
  
 Dans cette procédure pas à pas, vous exécuterez la commande suivante :  
  
-   Créer un assembly avec nom fort qui possède une interface publique qui contient des informations de type qui peuvent être incorporées.  
  
-   Créer un assembly de runtime avec nom fort qui implémente cette interface publique.  
  
-   Créer un programme client qui incorpore les informations de type à partir de l’interface publique et crée une instance de la classe de l’assembly de runtime.  
  
-   Modifier et régénérer l’assembly de runtime.  
  
-   Exécutez le programme client pour vérifier que la nouvelle version de l’assembly de runtime est utilisée sans avoir à recompiler le programme client.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a>Création d’une Interface  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Pour créer le projet d’interface de type équivalence  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue le **Types de projet** volet, assurez-vous que **Windows** est sélectionnée. Sélectionnez **bibliothèque de classes** dans les **modèles** volet. Dans le **nom** , tapez `TypeEquivalenceInterface`, puis cliquez sur **OK**. Le nouveau projet est créé.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**. Renommez le fichier `ISampleInterface.vb` et appuyez sur ENTRÉE. Renommer le fichier sera également renommer la classe `ISampleInterface`. Cette classe représente l’interface publique de la classe.  
  
4.  Cliquez sur le projet TypeEquivalenceInterface, puis cliquez sur **propriétés**. Cliquez sur l’onglet **Compiler**. Définir le chemin de sortie à un emplacement valide sur votre ordinateur de développement, telles que `C:\TypeEquivalenceSample`. Cet emplacement doit également être utilisé dans une étape ultérieure de cette procédure pas à pas.  
  
5.  Tout en modifiant les propriétés du projet, cliquez sur le **signature** onglet. Sélectionnez le **signer l’assembly** option. Dans le **choisir un fichier de clé de nom fort** , cliquez sur ** <New...> **.</New...> Dans le **nom de fichier de clé** , tapez `key.snk`. Désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher. Cliquez sur **OK**.  
  
6.  Ouvrez le fichier ISampleInterface.vb. Ajoutez le code suivant au fichier ISampleInterface pour créer l’interface ISampleInterface.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
7.  Sur le **outils** menu, cliquez sur **créer un Guid**. Dans le **créer un GUID** boîte de dialogue, cliquez sur **au Format de Registre** , puis **copie**. Cliquez sur **Quitter**.  
  
8.  Dans le `Guid` d’attribut, supprimez l’exemple de GUID et collez le GUID que vous avez copié à partir de la **créer un GUID** boîte de dialogue. Supprimez les accolades ({}) du GUID copié.  
  
9. Sur le **projet** menu, cliquez sur **afficher tous les fichiers**.  
  
10. Dans **l’Explorateur de solutions**, développez le **mon projet** dossier. Double-cliquez sur le AssemblyInfo.vb. Ajoutez l’attribut suivant au fichier.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     Enregistrez le fichier.  
  
11. Enregistrez le projet.  
  
12. Cliquez sur le projet TypeEquivalenceInterface, puis cliquez sur **Build**. Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de génération spécifié (par exemple, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Création d’une classe d’exécution  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Pour créer le projet de runtime d’équivalence de type  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue le **Types de projet** volet, assurez-vous que **Windows** est sélectionnée. Sélectionnez **bibliothèque de classes** dans les **modèles** volet. Dans le **nom** , tapez `TypeEquivalenceRuntime`, puis cliquez sur **OK**. Le nouveau projet est créé.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**. Renommez le fichier `SampleClass.vb` et appuyez sur ENTRÉE. Renommer le fichier renomme également la classe `SampleClass`. Cette classe implémente le `ISampleInterface` interface.  
  
4.  Cliquez sur le projet TypeEquivalenceRuntime et cliquez sur **propriétés**. Cliquez sur l’onglet **Compiler**. Définir le chemin de sortie vers le même emplacement que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple, `C:\TypeEquivalenceSample`.  
  
5.  Tout en modifiant les propriétés du projet, cliquez sur le **signature** onglet. Sélectionnez le **signer l’assembly** option. Dans le **choisir un fichier de clé de nom fort** , cliquez sur ** <New...> **.</New...> Dans le **nom de fichier de clé** , tapez `key.snk`. Désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher. Cliquez sur **OK**.  
  
6.  Cliquez sur le projet TypeEquivalenceRuntime et cliquez sur **ajouter une référence**. Cliquez sur le **Parcourir** onglet et accédez au dossier du chemin de sortie. Sélectionnez le fichier TypeEquivalenceInterface.dll et cliquez sur **OK**.  
  
7.  Sur le **projet** menu, cliquez sur **afficher tous les fichiers**.  
  
8.  Dans **l’Explorateur de solutions**, développez le **références** dossier. Sélectionnez la référence TypeEquivalenceInterface. Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la **Version spécifique** propriété **False**.  
  
9. Ajoutez le code suivant au fichier de classe SampleClass pour créer la classe SampleClass.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
10. Enregistrez le projet.  
  
11. Cliquez sur le projet TypeEquivalenceRuntime et cliquez sur **Build**. Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de génération spécifié (par exemple, C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Création d’un projet Client  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Pour créer le projet client équivalence des types  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue le **Types de projet** volet, assurez-vous que **Windows** est sélectionnée. Sélectionnez **Application Console** dans les **modèles** volet. Dans le **nom** , tapez `TypeEquivalenceClient`, puis cliquez sur **OK**. Le nouveau projet est créé.  
  
3.  Cliquez sur le projet TypeEquivalenceClient, puis cliquez sur **propriétés**. Cliquez sur l’onglet **Compiler**. Définir le chemin de sortie vers le même emplacement que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple, `C:\TypeEquivalenceSample`.  
  
4.  Cliquez sur le projet TypeEquivalenceClient, puis cliquez sur **ajouter une référence**. Cliquez sur le **Parcourir** onglet et accédez au dossier du chemin de sortie. Sélectionnez le fichier TypeEquivalenceInterface.dll (pas le fichier TypeEquivalenceRuntime.dll) et cliquez sur **OK**.  
  
5.  Sur le **projet** menu, cliquez sur **afficher tous les fichiers**.  
  
6.  Dans **l’Explorateur de solutions**, développez le **références** dossier. Sélectionnez la référence TypeEquivalenceInterface. Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la **incorporer les Types Interop** propriété **True**.  
  
7.  Ajoutez le code suivant au fichier Module1.vb pour créer le programme client.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
8.  Appuyez sur CTRL + F5 pour générer et exécuter le programme.  
  
## <a name="modifying-the-interface"></a>Modification de l’Interface  
  
#### <a name="to-modify-the-interface"></a>Pour modifier l’interface  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **Open**, puis cliquez sur **projet/Solution**.  
  
2.  Dans le **ouvrir un projet** boîte de dialogue, cliquez sur le projet TypeEquivalenceInterface, puis cliquez sur **propriétés**. Cliquez sur l’onglet **Application** . Cliquez sur le **informations de l’Assembly** bouton. Modifier la **Version de l’Assembly** et **Version du fichier** des valeurs `2.0.0.0`.  
  
3.  Ouvrez le fichier ISampleInterface.vb. Ajoutez la ligne de code suivante à l’interface ISampleInterface.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     Enregistrez le fichier.  
  
4.  Enregistrez le projet.  
  
5.  Cliquez sur le projet TypeEquivalenceInterface, puis cliquez sur **Build**. Une nouvelle version du fichier .dll de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de génération spécifié (par exemple, C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Modification de la classe d’exécution  
  
#### <a name="to-modify-the-runtime-class"></a>Pour modifier la classe d’exécution  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **Open**, puis cliquez sur **projet/Solution**.  
  
2.  Dans le **ouvrir un projet** boîte de dialogue, cliquez sur le projet TypeEquivalenceRuntime et cliquez sur **propriétés**. Cliquez sur l’onglet **Application** . Cliquez sur le **informations de l’Assembly** bouton. Modifier la **Version de l’Assembly** et **Version du fichier** des valeurs `2.0.0.0`.  
  
3.  Ouvrez la SampleClass.vbfile. Ajoutez les lignes de code suivantes à la classe SampleClass.  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  Enregistrez le projet.  
  
5.  Cliquez sur le projet TypeEquivalenceRuntime et cliquez sur **Build**. Une version mise à jour du fichier .dll de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de génération précédemment spécifié (par exemple, C:\TypeEquivalenceSample).  
  
6.  Dans l’Explorateur de fichiers, ouvrez le dossier de chemin de sortie (par exemple, C:\TypeEquivalenceSample). Double-cliquez sur le TypeEquivalenceClient.exe pour exécuter le programme. Le programme reflétera la nouvelle version de l’assembly TypeEquivalenceRuntime sans recompilation.  
  
## <a name="see-also"></a>Voir aussi  
 [/Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)   
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Programmation avec des assemblys](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)

