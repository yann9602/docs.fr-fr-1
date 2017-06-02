---
title: "Cr&#233;ation de fichiers de ressources pour les applications bureautiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers .resources"
  - "ressources d'application, créer des fichiers"
  - "fichiers de ressources, fichiers .resources"
  - "fichiers de ressources, créer"
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
caps.latest.revision: 25
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 25
---
# Cr&#233;ation de fichiers de ressources pour les applications bureautiques
Vous pouvez inclure des ressources, telles que des chaînes, des images ou des données d'objet, dans les fichiers de ressources pour que votre application puisse facilement y accéder.  Le .NET Framework offre cinq façons de créer des fichiers de ressources :  
  
-   Créez un fichier texte qui contient des ressources de type chaîne.  Vous pouvez utiliser l'[Outil Resource File Generator Tool \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour convertir le fichier texte en un fichier de ressources binaire \(.resources\).  Vous pouvez ensuite incorporer le fichier de ressources binaire dans un exécutable d'application ou une bibliothèque d'applications en utilisant un compilateur de langage, ou l'incorporer dans un assembly satellite à l'aide d'[Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  Pour plus d'informations, consultez la section [Ressources dans les fichiers texte](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles).  
  
-   Créez un fichier de ressources \(.resx\) XML qui contient des données de chaîne, d'image ou d'objet.  Vous pouvez utiliser l'[Outil Resource File Generator Tool \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour convertir le fichier .resx en un fichier de ressources binaire \(.resources\).  Vous pouvez ensuite incorporer le fichier de ressources binaire dans un exécutable d'application ou une bibliothèque d'applications en utilisant un compilateur de langage, ou l'incorporer dans un assembly satellite à l'aide d'[Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  Pour plus d'informations, consultez la section [Ressources dans les fichiers .resx](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles).  
  
-   Créez un fichier de ressource \(.resx\) XML par programmation en utilisant des types dans l'espace de noms <xref:System.Resources>.  Vous pouvez créer un fichier .resx, énumérer ses ressources et récupérer des ressources spécifiques par nom.  Pour plus d'informations, consultez la rubrique [Utilisation des fichiers .resx par programmation](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
-   Créez un fichier de ressources binaire \(.resources\) par programmation.  Vous pouvez ensuite incorporer le fichier dans un exécutable d'application ou une bibliothèque d'applications en utilisant un compilateur de langage, ou l'incorporer dans un assembly satellite à l'aide d'[Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  Pour plus d'informations, consultez la section [Ressources dans les fichiers .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles).  
  
-   Utilisez Visual Studio pour créer un fichier de ressources et l'inclure dans votre projet.  Visual Studio fournit un éditeur de ressources qui vous permet d'ajouter, de supprimer et de modifier des ressources.  Au moment de la compilation, le fichier de ressources est converti automatiquement en un fichier .resources binaire et incorporé dans un assembly d'application ou assembly satellite.  Pour plus d'informations, consultez la section [Fichiers de ressources dans Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles).  
  
<a name="TextFiles"></a>   
## Ressources dans les fichiers texte  
 Utilisez des fichiers texte \(.txt ou .restext\) pour stocker vos ressources de type chaîne uniquement. Pour vos ressources qui ne sont pas des chaînes, utilisez des fichiers .resx ou créez\-les par programmation.  Les fichiers texte qui contiennent des ressources de type chaîne ont le format suivant :  
  
```  
# This is an optional comment.  
name = value  
  
; This is another optional comment.  
name = value  
  
; The following supports conditional compilation if X is defined.  
#ifdef X  
name1=value1  
name2=value2  
#endif  
  
# The following supports conditional compilation if Y is undefined.  
#if !Y  
name1=value1  
name2=value2  
#endif  
  
```  
  
 Le format de fichier de ressources des fichiers .txt et de .restext est identique.  L'extension de fichier .restext sert uniquement à rendre des fichiers texte immédiatement identifiables comme fichiers de ressources textuelles.  
  
 Les ressources de type chaîne s'affichent sous forme de paires *name\/value*, où *name* est une chaîne qui identifie la ressource, et *value* est la chaîne de ressource retournée lorsque vous passez *name* à une méthode de récupération de la ressource telle que <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>.  *name* et *value* doivent être séparés par un signe égal \(\=\).  Par exemple :  
  
```  
  
FileMenuName=File  
EditMenuName=Edit  
ViewMenuName=View  
HelpMenuName=Help  
  
```  
  
> [!CAUTION]
>  N'utilisez pas de fichiers de ressources pour stocker des mots de passe, des informations sensibles ou des données privées.  
  
 Les chaînes vides \(autrement dit, une ressource dont la valeur est <xref:System.String.Empty?displayProperty=fullName>\) sont autorisées dans les fichiers texte.  Par exemple :  
  
```  
EmptyString=  
```  
  
 Depuis [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les fichiers texte prennent en charge la compilation conditionnelle avec `#ifdef` *symbol*…  `#endif` et `#if !`*symbol*…  constructions `#endif`.  Vous pouvez ensuite utiliser le commutateur `/define` avec [Générateur de fichiers ressource \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour définir les symboles.  Chaque ressource requiert son propre `#ifdef` *symbol*...  `#endif` ou `#if !`*symbol*...  Contruction `#endif`.  Si vous utilisez une instruction `#ifdef` et *symbol* est défini, la ressource associée est incluse dans le fichier .resources ; sinon, elle n'est pas incluse.  Si vous utilisez une instruction `#if !` et *symbol* n'est pas défini, la ressource associée est incluse dans le fichier .resources ; sinon, elle n'est pas incluse.  
  
 Les commentaires sont facultatifs dans les fichiers texte et sont précédés par un point\-virgule \(;\) ou par un signe dièse \(\#\) au début d'une ligne.  Les lignes qui contiennent des commentaires peuvent être placées n'importe où dans le fichier.  Les commentaires ne sont pas inclus dans un fichier .resources compilé créé à l'aide du [générateur de fichiers ressource \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Les lignes vides dans les fichiers texte sont considérées comme des espaces blancs et sont ignorées.  
  
 L'exemple suivant définit deux ressources de type chaîne nommées `OKButton` et `CancelButton`.  
  
```  
#Define resources for buttons in the user interface.  
OKButton=OK  
CancelButton=Cancel  
```  
  
 Si le fichier texte contient des occurrences en double de *name*, le [Générateur de Fichiers Ressource \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) affiche un avertissement et ignore le deuxième nom.  
  
 *value* ne peut pas contenir de caractères de nouvelle ligne, mais vous pouvez utiliser des caractères d'échappement dans le style du langage C, tels que `\n` pour représenter une nouvelle ligne et `\t` pour représenter un onglet.  Vous pouvez également inclure une barre oblique inverse si elle est échappée \(par exemple, "\\\\"\).  De plus, une chaîne vide est autorisée.  
  
 Il est préférable d'enregistrer les ressources au format de fichier texte en utilisant l'encodage UTF\-8 ou UTF\-16 dans un ordre d'octet avec primauté des octets de poids faible \(little\-endian\) ou un ordre d'octet avec primauté des octets de poids fort \(big\-endian\).  Toutefois, l'[Outil Resource File Generator Tool \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), qui convertit un fichier .txt en un fichier .resources, traite par défaut des fichiers comme UTF\-8.  Si vous souhaitez que Resgen.exe reconnaisse un fichier encodé à l'aide d'UTF\-16, vous devez inclure une marque d'ordre d'octet Unicode \(U\+FEFF\) au début du fichier.  
  
 Pour incorporer un fichier de ressources au format de fichier texte dans un assembly .NET Framework, vous devez convertir le fichier en un fichier de ressources binaire \(.resources\) à l'aide de l'[Outil Resource File Generator Tool \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  Vous pouvez incorporer ensuite le fichier .resources dans un assembly .NET Framework à l'aide d'un compilateur de langage ou l'incorporer dans un assembly satellite à l'aide d'[Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 L'exemple suivant utilise un fichier de ressources au format texte nommé GreetingResources.txt pour une application console « Hello World » simple.  Le fichier texte définit deux chaînes, `prompt` et `greeting`, qui invitent l'utilisateur à entrer son nom et affichent un message d'accueil.  
  
```  
# GreetingResources.txt   
# A resource file in text format for a "Hello World" application.  
#  
# Initial prompt to the user.  
prompt=Enter your name:   
# Format string to display the result.  
greeting=Hello, {0}!  
```  
  
 Le fichier texte est converti en un fichier .resources à l'aide de la commande suivante :  
  
 **resgen GreetingResources.txt**  
  
 L'exemple suivant affiche le code source pour une application console qui utilise le fichier .resources pour afficher des messages à l'utilisateur.  
  
 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]  
  
 Si vous utilisez Visual Basic, et que le fichier de code source est nommé Greeting.vb, la commande suivante crée un fichier exécutable qui inclut le fichier .resources incorporé :  
  
 **vbc greeting.vb \/resource:GreetingResources.resources**  
  
 Si vous utilisez C\#, et que le fichier de code source est nommé Greeting.cs, la commande suivante crée un fichier exécutable qui inclut le fichier .resources incorporé :  
  
 **csc greeting.cs \/resource:GreetingResources.resources**  
  
<a name="ResxFiles"></a>   
## Ressources dans les fichiers .resx  
 Contrairement aux fichiers texte, qui peuvent stocker des ressources de type chaîne uniquement, les fichiers de ressources XML \(.resx\) peuvent stocker des chaînes, des données binaires telles que les images, les icônes, les clips audio et les objets de programmation.  Un fichier .resx contient un en\-tête standard, qui décrit le format des entrées de ressources et spécifie les informations de contrôle de version pour le XML utilisé pour analyser les données.  Les données de fichier de ressources suivent l'en\-tête XML.  Chaque élément de données se compose d'une paire nom\/valeur contenue dans une balise `data`.  Son attribut `name` définit le nom de ressource et la balise `value` imbriquée contient la valeur de ressource.  Pour les données de type chaîne, la balise `value` contient la chaîne.  
  
 Par exemple, la balise `data` suivante définit une ressource de type chaîne nommée `prompt` dont la valeur est « ENTREZ votre nom : ».  
  
```  
<data name="prompt" xml:space="preserve">  
  <value>Enter your name:</value>  
</data>  
```  
  
> [!WARNING]
>  N'utilisez pas de fichiers de ressources pour stocker des mots de passe, des informations sensibles ou des données privées.  
  
 Pour les objets de ressource, la balise **données** inclut un attribut `type` qui indique le type de données de la ressource.  Pour les objets qui se composent de données binaires, la balise `data` inclut également un attribut `mimetype`, qui indique le type `base64` des données binaires.  
  
> [!NOTE]
>  Tous les fichiers .resx utilisent un formateur de sérialisation binaire pour générer et analyser les données binaires d'un type spécifié.  Par conséquent, un fichier .resx peut devenir non valide si le format de sérialisation binaire d'un objet change d'une manière non compatible.  
  
 L'exemple suivant affiche une partie d'un fichier .resx qui inclut une ressource <xref:System.Int32> et une image bitmap.  
  
```  
  
<data name="i1" type="System.Int32, mscorlib">  
  <value>20</value>  
</data>  
  
<data name="flag" type="System.Drawing.Bitmap, System.Drawing,     
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
    mimetype="application/x-microsoft.net.object.bytearray.base64">  
  <value>  
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…  
  </value>  
</data>  
```  
  
> [!IMPORTANT]
>  Étant donné que les fichiers .resx doivent se composer de code XML bien formé dans un format prédéfini, nous déconseillons d'utiliser des fichiers .resx manuellement, en particulier lorsque les fichiers .resx contiennent des ressources autres que des chaînes.  À la place, Visual Studio fournit une interface transparente pour la création et la manipulation de fichiers .resx. Pour plus d'informations, consultez la section [Fichiers de ressources dans Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles).  Vous pouvez également créer et manipuler des fichiers .resx par programmation.  Pour plus d'informations, consultez [Utilisation des fichiers .resx par programmation](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
<a name="ResourcesFiles"></a>   
## Ressources dans les fichiers .resources  
 Vous pouvez utiliser la classe <xref:System.Resources.ResourceWriter?displayProperty=fullName> pour créer par programmation un fichier de ressources binaire \(.resources\) directement à partir du code.  Vous pouvez également utiliser l'[Outil Resource File Generator Tool \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour créer un fichier .resources à partir d'un fichier texte ou d'un fichier .resx.  Le fichier .resources peut contenir des données binaires \(tableaux d'octets\) et des données d'objet en plus de données de type chaîne.  La création d'un fichier .resources par programmation requiert les étapes suivantes :  
  
1.  Créez un objet <xref:System.Resources.ResourceWriter> avec un nom de fichier unique.  Vous pouvez le faire en spécifiant un nom de fichier ou un flux de fichiers pour un constructeur de classe <xref:System.Resources.ResourceWriter>.  
  
2.  Appelez une des surcharges de la méthode <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=fullName> pour chaque ressource nommée à ajouter au fichier.  La ressource peut être une chaîne, un objet ou une collection de données binaires \(tableau d'octets\).  
  
3.  Appelez la méthode <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=fullName> pour écrire les ressources dans le fichier et fermer l'objet <xref:System.Resources.ResourceWriter>.  
  
> [!NOTE]
>  N'utilisez pas de fichiers de ressources pour stocker des mots de passe, des informations sensibles ou des données privées.  
  
 L'exemple suivant crée par programmation un fichier .resources nommé CarResources.resources qui stocke six chaînes, une icône et deux objets définis par l'application \(deux objets `Automobile` \).  Notez que la classe `Automobile`, définie et instanciée dans l'exemple, est marquée avec l'attribut <xref:System.SerializableAttribute>, qui lui permet d'être rendue persistante par le formateur de sérialisation binaire.  
  
 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]  
  
 Une fois que vous avez créé le fichier .resources, vous pouvez l'incorporer dans un fichier exécutable à l'exécution ou une bibliothèque en incluant le commutateur `/resource` du compilateur de langage, ou l'incorporer dans un assembly satellite à l'aide d'[Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
<a name="VSResFiles"></a>   
## Fichiers de ressources dans Visual Studio  
 Lorsque vous ajoutez un fichier de ressources à votre projet Visual Studio, Visual Studio crée un fichier .resx dans le répertoire de projet.  Visual Studio fournit des éditeurs de ressources qui vous permettent d'ajouter des chaînes, des images et des objets binaires.  Étant donné que les éditeurs sont conçus pour gérer des données statiques uniquement, ils ne peuvent pas être utilisés pour stocker des objets de programmation. Vous devez écrire par programmation les données d'objet dans un fichier .resx ou .resources.  Consultez la rubrique [Utilisation des fichiers .resx par programmation](../../../docs/framework/resources/working-with-resx-files-programmatically.md) et la section [Ressources dans les fichiers .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) pour plus d'informations.  
  
 Si vous ajoutez des ressources localisées, vous devez leur donner le même nom de fichier racine que le fichier de ressources principal et désigner leur culture dans le nom du fichier.  Par exemple, si vous ajoutez un fichier de ressources nommé Resources.resx, vous pouvez créer également les fichiers de ressources nommés Resources.en\-US.resx et Resources.fr\-FR.resx pour y stocker des ressources localisées pour les cultures Anglais \(États\-Unis\) et Français \(France\), respectivement.  Vous devez également désigner la culture par défaut de votre application.  C'est la culture dont les ressources sont utilisées si aucune ressource localisée pour une culture particulière n'est trouvée.  Pour spécifier la culture par défaut, dans l'Explorateur de solutions dans Visual Studio, cliquez avec le bouton droit sur le nom du projet, pointez sur l'application, cliquez sur **Informations de l'assembly** et sélectionnez la langue\/culture appropriée dans la liste **Langage neutre**.  
  
 Au moment de la compilation, Visual Studio convertit en premier les fichiers .resx dans un projet en fichiers de ressources binaires \(.resources\) et les stocke dans un sous\-répertoire du répertoire obj du projet.  Visual Studio incorpore tous les fichiers de ressources qui ne contiennent pas de ressources localisées dans l'assembly principal généré par le projet.  Si des fichiers de ressources contiennent des ressources localisées, Visual Studio les incorpore dans des assemblys satellites séparés pour chaque culture localisée.  Il stocke alors chaque assembly satellite dans un répertoire dont le nom correspond à la culture localisée.  Par exemple, les ressources Anglais \(États\-Unis\) localisées sont stockées dans un assembly satellite dans le sous\-répertoire en\-US.  
  
## Voir aussi  
 <xref:System.Resources>   
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)   
 [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)