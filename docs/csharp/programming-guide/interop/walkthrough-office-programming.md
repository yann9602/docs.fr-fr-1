---
title: "Proc&#233;dure pas &#224; pas&#160;: programmation Office (C# et Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "programmation Office (C#)"
  - "programmation Office (Visual Basic)"
  - "Office, programmation dans Visual Basic et C#"
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
caps.latest.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 46
---
# Proc&#233;dure pas &#224; pas&#160;: programmation Office (C# et Visual Basic)
[!INCLUDE[vs_dev10_long](../../../csharp/programming-guide/interop/includes/vs-dev10-long-md.md)] présente les nouvelles fonctionnalités de C\# et de Visual Basic qui améliorent la programmation Microsoft Office.  Chaque langage a ajouté des fonctionnalités déjà existantes dans l'autre langage.  
  
 Les nouvelles fonctionnalités de C\# incluent les arguments nommés et les arguments facultatifs, les valeurs de retour dont le type est `dynamic`, et, en programmation COM, la possibilité d'omettre le mot clé `ref` et d'accéder aux propriétés indexées.  Les nouvelles fonctionnalités de Visual Basic incluent les propriétés implémentées automatiquement, les instructions dans les expressions lambda et les initialiseurs de collection.  
  
 Les deux langages autorisent l'incorporation d'informations de type, qui permet de déployer des assemblys interagissant avec les composants COM sans déployer les assemblys PIA \(Primary Interop Assemblies\) sur l'ordinateur de l'utilisateur.  Pour plus d'informations, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Cette procédure pas à pas montre les nouvelles fonctionnalités dans le contexte de la programmation Office, mais beaucoup d'entre elles sont aussi utiles en programmation générale.  Dans la procédure pas à pas, vous utiliserez d'abord une application de type complément Excel pour créer un classeur Excel.  Vous allez ensuite créer un document Word contenant un lien vers le classeur.  Enfin, vous découvrirez comment activer ou désactiver la dépendance d'assembly PIA.  
  
## Composants requis  
 Microsoft Office Excel 2013 \(ou version 2007 ou ultérieure\) et Microsoft Office Word 2013 \(ou version 2007 ou ultérieure\) doivent être installés sur votre ordinateur pour que vous puissiez exécuter cette procédure pas à pas.  
  
 Si vous utilisez un système d'exploitation antérieur à [!INCLUDE[windowsver](../../../csharp/programming-guide/interop/includes/windowsver-md.md)], assurez\-vous que [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] est installé.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour configurer une application de type complément Excel  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet **Modèles installés**, développez **Visual Basic** ou **Visual C\#**, développez **Office**, puis cliquez sur **2013** \(ou **2010** ou **2007**\).  
  
4.  Dans le volet **Modèles**, cliquez sur **Complément Excel 2013** \(ou **Complément Excel 2010** ou **Complément Excel 2007**\).  
  
5.  Regardez en haut du volet **Modèles** pour vous assurer que **.NET Framework 4**, ou version ultérieure, apparaît dans la zone **Framework cible**.  
  
6.  Si vous le désirez, entrez un nom pour votre projet dans la zone **Nom**.  
  
7.  Cliquez sur **OK**.  
  
8.  Le nouveau projet s'affiche dans l'**Explorateur de solutions**.  
  
### Pour ajouter des références  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**.  La boîte de dialogue **Ajouter une référence** s'affiche.  
  
2.  Sous l'onglet **Assemblys**, sélectionnez **Microsoft.Office.Interop.Excel**, version 15.0.0.0 \(ou version 14.0.0.0 pour Excel 2010 ou version 12.0.0.0 pour Excel 2007\), dans la liste **Nom du composant**, puis maintenez la touche CTRL enfoncée et sélectionnez **Microsoft.Office.Interop.Word**, version 15.0.0.0 \(ou version 14.0.0.0 pour Word 2010 ou 12.0.0.0 pour Word 2007\).  Si les assemblys n'apparaissent pas, vous devez vous assurer qu'ils sont installés et s'affichent \(voir [Comment : installer les assemblys PIA \(Primary Interop Assembly\) d'Office](../Topic/How%20to:%20Install%20Office%20Primary%20Interop%20Assemblies.md)\).  
  
3.  Cliquez sur **OK**.  
  
### Pour ajouter les instructions Imports ou les directives using nécessaires  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **ThisAddIn.vb** ou **ThisAddIn.cs**, puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez les instructions `Imports` suivantes \(Visual Basic\) ou les directives `using` \(C\#\) en haut du fichier de code, si elles ne sont pas déjà présentes.  
  
     [!code-cs[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#1)]
     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#1)]  
  
### Pour créer une liste de comptes bancaires  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, cliquez sur **Ajouter**, puis sur **Classe**.  Nommez la classe Account.vb si vous utilisez Visual Basic ou Account.cs si vous utilisez C\#.  Cliquez sur **Ajouter**.  
  
2.  Remplacez la définition de la classe `Account` par le code suivant :  Les définitions de classe utilisent les *propriétés implémentées automatiquement* \(nouveauté en Visual Basic dans Visual Studio 2010\).  Pour plus d'informations, consultez [Auto\-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-cs[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/account.cs#2)]
     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/account.vb#2)]  
  
3.  Pour créer une liste `bankAccounts` qui contient deux comptes, ajoutez le code suivant à la méthode `ThisAddIn_Startup` dans ThisAddIn.vb ou ThisAddIn.cs.  Les déclarations de liste utilisent les *initialiseurs de collection* \(nouveauté en Visual Basic dans Visual Studio 2010\).  Pour plus d'informations, consultez [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-cs[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#3)]
     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#3)]  
  
### Pour exporter des données vers Excel  
  
1.  Dans le même fichier, ajoutez la méthode suivante à la classe `ThisAddIn`.  La méthode configure un classeur Excel, vers lequel elle exporte les données.  
  
     [!code-cs[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#4)]
     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#4)]  
  
     Deux nouvelles fonctionnalités C\# sont utilisées dans cette méthode.  Ces deux fonctionnalités existent déjà en Visual Basic.  
  
    -   La méthode [Add](http://go.microsoft.com/fwlink/?LinkId=210910) possède un *paramètre facultatif* pour spécifier un modèle particulier.  Les paramètres optionnels, introduits dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], vous permettent d'omettre l'argument du paramètre, si vous souhaitez utiliser la valeur par défaut de ce dernier.  Dans la mesure où aucun argument n'est envoyé dans l'exemple précédent, `Add` utilise le modèle par défaut et crée un classeur.  L'instruction équivalente dans les versions antérieures de C\# nécessite un argument d'espace réservé : `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Pour plus d'informations, consultez [Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   Les propriétés `Range` et `Offset` de l'objet [Range](http://go.microsoft.com/fwlink/?LinkId=210911) utilisent la fonctionnalité des *propriétés indexées*.  Cette fonctionnalité vous permet de consommer ces propriétés à partir des types COM à l'aide de la syntaxe C\# standard suivante.  Les propriétés indexées vous permettent également d'utiliser la propriété `Value` de l'objet `Range`, ce qui rend superflue l'utilisation de la propriété `Value2`.  La propriété `Value` est indexée, mais l'index est optionnel.  Les arguments facultatifs et les propriétés indexées fonctionnent ensemble dans l'exemple suivant.  
  
         [!code-cs[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#5)]  
  
         Dans les versions antérieures du langage, la syntaxe spéciale suivante est requise.  
  
         [!code-cs[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#6)]  
  
         Vous ne pouvez pas créer vos propres propriétés indexées.  La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.  
  
         Pour plus d'informations, consultez [Comment : utiliser des propriétés indexées dans la programmation COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  À la fin de `DisplayInExcel`, ajoutez le code suivant pour ajuster les largeurs de colonne au contenu.  
  
     [!code-cs[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#7)]
     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#7)]  
  
     Ces ajouts illustrent une autre fonctionnalité nouvelle de C\# 2010 : traiter les valeurs `Object` retournées par les hôtes COM tels qu'Office comme si leur type était [dynamic](../../../csharp/language-reference/keywords/dynamic.md).  Cela se produit automatiquement quand **incorporer les types interop** est défini à sa valeur par défaut, `True`, ou, de façon équivalente, lorsque l'assembly est référencé par l'option du compilateur [\/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md).  Le type `dynamic` permet la liaison tardive, déjà disponible en Visual Basic, et évite le cast explicite requis en Visual C\# 2008 et dans les versions antérieures du langage.  
  
     Par exemple, `excelApp.Columns[1]` retourne un `Object` et `AutoFit` est une méthode [Range](http://go.microsoft.com/fwlink/?LinkId=210911) Excel.  Sans `dynamic`, vous devez effectuer un cast de l'objet retourné par `excelApp.Columns[1]` sous la forme d'une instance de `Range` avant d'appeler la méthode `AutoFit`.  
  
     [!code-cs[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#8)]  
  
     Pour plus d'informations sur l'incorporation des types d'interopérabilité, consultez les procédures « Pour rechercher la référence d'assembly PIA » et « Pour restaurer la dépendance d'assembly PIA » plus loin dans cette rubrique.  Pour plus d'informations sur `dynamic`, consultez [dynamic](../../../csharp/language-reference/keywords/dynamic.md) ou [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### Pour appeler DisplayInExcel  
  
1.  Ajoutez le code suivant à la fin de la méthode `ThisAddIn_StartUp`.  L'appel à `DisplayInExcel` contient deux arguments.  Le premier argument est le nom de la liste des comptes à traiter.  Le deuxième argument est une expression lambda multiligne qui définit comment les données doivent être traitées.  Les valeurs `ID` et `balance` de chaque compte s'affichent dans des cellules adjacentes et la ligne s'affiche en rouge si le solde est inférieur à zéro.  Les expressions lambda multilignes sont une nouvelle fonctionnalité de Visual Basic 2010.  Pour plus d'informations, consultez [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-cs[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#9)]
     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#9)]  
  
2.  Pour exécuter le programme, appuyez sur F5.  Une feuille de calcul Excel s'affiche avec les données des comptes.  
  
### Pour ajouter un document Word  
  
1.  Ajoutez le code suivant à la fin de la méthode `ThisAddIn_StartUp` pour créer un document Word qui contient un lien vers le classeur Excel.  
  
     [!code-cs[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#10)]
     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/visualbasic/officewalkthroughsnippets - vb/thisaddin.vb#10)]  
  
     Ce code illustre plusieurs fonctionnalités nouvelles en C\# : la possibilité d'omettre le mot clé `ref` dans la programmation COM, les arguments nommés et les arguments facultatifs.  Ces fonctionnalités existent déjà en Visual Basic.  La méthode [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099) comporte sept paramètres, tous définis en tant que paramètres de référence optionnels.  Avant Visual C\# 2010, vous deviez définir les variables d'objet à utiliser comme arguments pour les sept paramètres, même si vous n'aviez aucune valeur significative à transmettre.  Les arguments nommés et les arguments facultatifs vous permettent de désigner les paramètres auxquels vous souhaitez accéder par leur nom et d'envoyer des arguments à ces seuls paramètres.  Dans cet exemple, les arguments sont envoyés pour indiquer qu'un lien vers le classeur dans le Presse\-papiers doit être créé \(paramètre `Link`\) et que ce lien doit être affiché dans le document Word sous forme d'une icône \(paramètre `DisplayAsIcon`\).  Visual C\# 2010 vous permet également d'omettre le mot clé `ref` pour ces arguments.  Comparez le segment de code suivant de Visual C\# 2008 et la ligne unique requise en Visual C\# 2010 :  
  
     [!code-cs[csOfficeWalkthrough#11](../../../csharp/programming-guide/interop/codesnippet/csharp/officewalkthroughcs/thisaddin.cs#11)]  
  
### Pour exécuter l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  Excel démarre et affiche un tableau qui contient les informations des deux comptes de `bankAccounts`.  Puis, un document Word apparaît qui contient un lien vers le tableau Excel.  
  
### Pour nettoyer le projet terminé  
  
1.  Dans Visual Studio, cliquez sur **Nettoyer la solution** dans le menu **Générer**.  Sinon, le complément s'exécutera chaque fois que vous ouvrirez Excel sur votre ordinateur.  
  
### Pour rechercher la référence d'assembly PIA  
  
1.  Exécutez de nouveau l'application, mais ne cliquez pas sur **Nettoyer la solution**.  
  
2.  Dans le menu **Démarrer**, cliquez sur **Tous les programmes**.  Puis, cliquez successivement sur **Microsoft Visual Studio 2013**, **Visual Studio Tools** et **Invite de commandes de Visual Studio \(2013\)**.  
  
3.  Entrez `ildasm` dans l'Invite de commandes de Visual Studio \(2013\), puis appuyez sur ENTRÉE.  La fenêtre IL DASM s'affiche.  
  
4.  Dans le menu **Fichier** de la fenêtre IL DASM, cliquez sur **Ouvrir**.  Double\-cliquez sur **Visual Studio 2013**, puis sur **Projets**.  Ouvrez le dossier de votre projet et, dans le dossier bin\/Debug, recherchez *nom de votre projet*.dll.  Double\-cliquez sur *nom de votre projet*.dll.  Une nouvelle fenêtre affiche les attributs de votre projet, en plus des références à d'autres modules et assemblys.  Remarquez que les espaces de noms `Microsoft.Office.Interop.Excel` et `Microsoft.Office.Interop.Word` sont inclus dans l'assembly.  Par défaut, dans Visual Studio 2013, le compilateur importe les types dont vous avez besoin à partir d'un assembly PIA référencé dans votre assembly.  
  
     Pour plus d'informations, consultez [Comment : afficher le contenu d'un assembly](../Topic/How%20to:%20View%20Assembly%20Contents.md).  
  
5.  Double\-cliquez sur l'icône **MANIFESTE**.  Une fenêtre affiche la liste des assemblys contenant les éléments référencés par le projet.  `Microsoft.Office.Interop.Excel` et `Microsoft.Office.Interop.Word` ne sont pas inclus dans la liste.  Étant donné que les types dont votre projet a besoin ont été importés dans votre assembly, les références à un assembly PIA ne sont pas requis.  Le déploiement s'en trouve facilité.  Les assemblys PIA ne doivent pas être présents sur l'ordinateur de l'utilisateur ; comme une application ne nécessite pas le déploiement d'une version spécifique d'un assembly PIA, les applications peuvent être conçues pour fonctionner avec plusieurs versions d'Office, sous réserve que les API nécessaires existent dans toutes les versions.  
  
     Le déploiement d'assemblys PIA n'étant plus nécessaire, vous pouvez créer une application dans les scénarios avancés qui fonctionne avec plusieurs versions d'Office, y compris les versions antérieures.  Cependant, cela ne fonctionne que si votre code n'utilise pas d'API qui ne sont pas disponibles dans la version d'Office que vous utilisez.  Comme il n'est pas toujours évident de savoir si une API particulière était disponible dans une version antérieure, l'utilisation de versions antérieures d'Office n'est pas recommandée.  
  
    > [!NOTE]
    >  Jusqu'à Office 2003, Office ne publiait pas les assemblys PIA.  Par conséquent, le seul moyen de générer un assembly d'interopérabilité pour Office 2002 ou versions antérieures consiste à importer la référence COM.  
  
6.  Fermez la fenêtre de manifeste et la fenêtre d'assembly.  
  
### Pour restaurer la dépendance d'assembly PIA  
  
1.  Dans l'**Explorateur de solutions**, choisissez **Afficher tous les fichiers**.  Développez le dossier **References** et sélectionnez **Microsoft.Office.Interop.Excel**.  Appuyez sur F4 pour afficher la fenêtre **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés**, modifiez la valeur de la propriété **Incorporer les types interop** de **True** en **False**.  
  
3.  Répétez les étapes 1 et 2 de cette procédure pour `Microsoft.Office.Interop.Word`.  
  
4.  Dans C\#, commentez les deux appels à `Autofit` à la fin de la méthode `DisplayInExcel`.  
  
5.  Appuyez sur F5 pour vérifier que le projet continue de s'exécuter correctement.  
  
6.  Répétez les étapes 1 à 3 de la procédure précédente pour ouvrir la fenêtre d'assembly.  Notez que `Microsoft.Office.Interop.Word` et `Microsoft.Office.Interop.Excel` ne sont plus dans la liste des assemblys incorporés.  
  
7.  Double\-cliquez sur l'icône **MANIFESTE** et faites défiler la liste des assemblys référencés.  `Microsoft.Office.Interop.Word` et `Microsoft.Office.Interop.Excel` figurent tous deux dans la liste.  Comme l'application référence les assemblys PIA Excel et Word, et que la propriété **Incorporer les types interop** a la valeur **False**, les deux assemblys doivent exister sur l'ordinateur de l'utilisateur final.  
  
8.  Dans Visual Studio, cliquez sur **Nettoyer la solution** dans le menu **Générer** pour nettoyer le projet achevé.  
  
## Voir aussi  
 [Auto\-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)   
 [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Comment : utiliser des propriétés indexées dans la programmation COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Interopérabilité](../../../csharp/programming-guide/interop/interoperability.md)