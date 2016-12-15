---
title: "G&#233;n&#233;ration &#224; partir de la ligne de commande avec csc.exe | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "générations (C#)"
  - "ligne de commande (C#)"
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# G&#233;n&#233;ration &#224; partir de la ligne de commande avec csc.exe
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez appeler le compilateur c# en tapant le nom de son fichier exécutable (csc.exe) à une invite de commandes.  
  
 Si vous utilisez la **Visual Studio Command Prompt** fenêtre, toutes les variables d’environnement nécessaires sont définies automatiquement. Dans Windows 7, vous pouvez accéder à cette fenêtre à partir de la **Démarrer** menu en ouvrant Microsoft Visual Studio *Version*dossier de \Visual Studio Tools. Dans Windows 8, l’invite de commandes Visual Studio est appelé le **invite de commandes développeur pour VS2012**, et vous pouvez le trouver en effectuant une recherche à partir de l’écran d’accueil.  
  
 Si vous utilisez une fenêtre d’invite de commande standard, vous devez ajuster votre chemin d’accès avant d’appeler csc.exe à partir de n’importe quel sous-répertoire de votre ordinateur. Vous devez également exécuter vsvars32.bat pour définir les variables d’environnement appropriées pour prendre en charge des versions de ligne de commande. Pour plus d’informations sur vsvars32.bat, y compris les instructions pour savoir comment trouver et exécuter, consultez [Comment : définir les Variables d’environnement pour la ligne de commande Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
 Si vous travaillez sur un ordinateur qui ne dispose que le [!INCLUDE[winsdklong](../../../csharp/language-reference/compiler-options/includes/winsdklong_md.md)], vous pouvez utiliser le compilateur Visual c# à le **invite de commandes SDK**, que vous pouvez ouvrir à partir de la **Microsoft .NET Framework SDK** option de menu.  
  
 Vous pouvez également utiliser MSBuild pour générer des programmes c# par programme. Pour plus d’informations, consultez [MSBuild](/visual-studio/msbuild/msbuild1).  
  
 Le fichier exécutable csc.exe se trouve généralement dans le NET\Framework\\*Version* dossier sous le répertoire Windows. Son emplacement peut varier selon la configuration exacte d’un ordinateur particulier. Si plusieurs versions du .NET Framework sont installée sur votre ordinateur, vous trouverez plusieurs versions de ce fichier. Pour plus d’informations sur ces installations, consultez [Détermination de la Version de l’infrastructure .NET est installée](http://msdn.microsoft.com/fr-fr/1a87cc6a-1c4b-4c38-b878-faa9b3beae3c).  
  
> [!TIP]
>  Lorsque vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher le **csc** commande et ses options de compilateur associé dans la **sortie** fenêtre. Pour afficher ces informations, suivez les instructions de [Comment : afficher, enregistrer et configurer les fichiers journaux Build](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md) pour modifier le niveau de détail des données de journal à **Normal** ou **détaillé**. Une fois que vous régénérez votre projet, recherchez le **sortie** fenêtre **csc** pour rechercher l’appel du compilateur c#.  
  
 **Dans cette rubrique.**  
  
-   [Règles pour la syntaxe de ligne de commande](#vcconcommand-linebuildinganchor1)  
  
-   [Exemples de lignes de commande](#vcconcommand-linebuildinganchor2)  
  
-   [Différences entre le compilateur c# et les résultats de la compilation C++](#vcconcommand-linebuildinganchor3)  
  
##  <a name="a-namevcconcommand-linebuildinganchor1a-rules-for-command-line-syntax-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor1"></a> Règles de syntaxe de ligne de commande pour le compilateur c#  
 Le compilateur c# utilise les règles suivantes lorsqu’il interprète les arguments spécifiés sur la ligne de commande du système d’exploitation :  
  
-   Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.  
  
-   L’accent circonflexe (^) n’est pas reconnu comme un caractère d’échappement ou du délimiteur. Ce caractère est géré par l’Analyseur de ligne de commande du système d’exploitation avant d’être passé au tableau argv du programme.  
  
-   Une chaîne entourée guillemets doubles (« chaîne ») est interprétée comme un argument unique, quel que soit l’espace blanc qui est contenue dans. Une chaîne entre guillemets peut être incorporée dans un argument.  
  
-   Un guillemet double précédé d’une barre oblique inverse (\\«) est interprété comme un caractère guillemet double littéral («).  
  
-   Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.  
  
-   Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau argv pour chaque paire de barres obliques inverses et le guillemet double est interprété comme un délimiteur de chaîne.  
  
-   Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le tableau argv pour chaque paire de barres obliques inverses et le guillemet double est « échappé » par la barre oblique inverse restante. Cela provoque un guillemet double littéral (") à ajouter argv.  
  
##  <a name="a-namevcconcommand-linebuildinganchor2a-sample-command-lines-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor2"></a> Exemples de lignes de commande pour le compilateur c#  
  
-   Compile File.cs pour produire File.exe :  
  
    ```  
    csc File.cs   
    ```  
  
-   Compile File.cs pour produire File.dll :  
  
    ```  
    csc /target:library File.cs  
    ```  
  
-   Compile File.cs et crée My.exe :  
  
    ```  
    csc /out:My.exe File.cs  
    ```  
  
-   Compile tous les fichiers c# dans le répertoire actif, avec les optimisations activées et définit le symbole DEBUG. La sortie est File2.exe :  
  
    ```  
    csc /define:DEBUG /optimize /out:File2.exe *.cs  
    ```  
  
-   Compile tous les fichiers c# dans le répertoire actif pour produire une version debug de File2.dll. Aucun logo ni aucun avertissement ne s’affichent :  
  
    ```  
    csc /target:library /out:File2.dll /warn:0 /nologo /debug *.cs  
    ```  
  
-   Compile tous les fichiers c# du répertoire actif vers Something.xyz (une DLL) :  
  
    ```  
    csc /target:library /out:Something.xyz *.cs  
    ```  
  
##  <a name="a-namevcconcommand-linebuildinganchor3a-differences-between-c-compiler-and-c-compiler-output"></a><a name="vcconcommand-linebuildinganchor3"></a> Différences entre le compilateur c# et les résultats de la compilation C++  
 Aucun fichier objet (.obj) créé par l’appel du compilateur c# ; fichiers de sortie sont créés directement. Par conséquent, le compilateur c# ne nécessite pas d’un éditeur de liens.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur c#](../../../csharp/language-reference/compiler-options/index.md)   
 [Options du compilateur c# par ordre alphabétique](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [Options du compilateur c# par catégorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Main() et Arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)   
 [Comment : afficher les Arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Comment : accéder à des Arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)