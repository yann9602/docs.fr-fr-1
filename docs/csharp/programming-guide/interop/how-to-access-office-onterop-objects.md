---
title: "Comment&#160;: acc&#233;der aux objets Office Interop &#224; l&#39;aide des fonctionnalit&#233;s Visual&#160;C# (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "dynamic (C#), programmation Office"
  - "arguments nommés et facultatifs (C#), programmation Office"
  - "arguments nommés (C#), programmation Office"
  - "programmation Office (C#)"
  - "arguments facultatifs (C#), programmation Office"
  - "paramètres facultatifs (C#), programmation Office"
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
caps.latest.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 33
---
# Comment&#160;: acc&#233;der aux objets Office Interop &#224; l&#39;aide des fonctionnalit&#233;s Visual&#160;C# (Guide de programmation&#160;C#)
Visual C\# 2010 introduit de nouvelles fonctionnalités qui simplifient l'accès aux objets d'API Office.  Les nouvelles fonctionnalités incluent les arguments nommés et les arguments facultatifs, un nouveau type appelé `dynamic` et la possibilité de passer des arguments aux paramètres de référence dans les méthodes COM comme s'il s'agissait de paramètres de valeur.  
  
 Dans cette rubrique, vous allez utiliser les nouvelles fonctionnalités pour écrire le code qui crée et affiche une feuille de calcul Microsoft Office Excel.  Vous écrirez ensuite le code pour ajouter un document Office Word qui contient une icône liée à la feuille de calcul Excel.  
  
 Pour effectuer cette procédure pas à pas, Microsoft Office Excel 2007 et Microsoft Office Word 2007, ou versions ultérieures, doivent être installés sur votre ordinateur.  
  
 Si vous utilisez un système d'exploitation antérieur à [!INCLUDE[windowsver](../../../csharp/programming-guide/interop/includes/windowsver-md.md)], assurez\-vous que [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] est installé.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour créer une application console  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Modèles installés**, développez **Visual C\#**, puis cliquez sur **Windows**.  
  
4.  Vérifiez en haut de la boîte de dialogue **Nouveau projet** que **.NET Framework 4** \(ou version ultérieure\) est sélectionné comme framework cible.  
  
5.  Dans le volet **Modèles**, cliquez sur **Application console**.  
  
6.  Attribuez un nom à votre projet dans le champ **Nom**.  
  
7.  Cliquez sur **OK**.  
  
     Le nouveau projet s'affiche dans l'**Explorateur de solutions**.  
  
### Pour ajouter des références  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**.  La boîte de dialogue **Ajouter une référence** s'affiche.  
  
2.  Dans la page **Assemblys** e, sélectionnez **Microsoft.Office.Interop.Word** dans la liste **Nom du composant**, puis maintenez la touche CTRL enfoncée et sélectionnez **Microsoft.Office.Interop.Excel**.  Si les assemblys n'apparaissent pas, vous devez vous assurer qu'ils sont installés et s'affichent \(voir [Comment : installer les assemblys PIA \(Primary Interop Assembly\) d'Office](../Topic/How%20to:%20Install%20Office%20Primary%20Interop%20Assemblies.md)\)  
  
3.  Cliquez sur **OK**.  
  
### Pour ajouter les directives using nécessaires  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **Program.cs**, puis cliquez sur **Afficher le code**.  
  
2.  Ajoutez les directives `using` suivantes en début du fichier de code.  
  
     [!code-cs[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]  
  
### Pour créer une liste de comptes bancaires  
  
1.  Collez la définition de classe suivante dans **Program.cs**, sous la classe `Program`.  
  
     [!code-cs[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]  
  
2.  Ajoutez le code suivant à la méthode `Main` pour créer une liste `bankAccounts` contenant deux comptes.  
  
     [!code-cs[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]  
  
### Pour déclarer une méthode qui exporte les informations de compte vers Excel  
  
1.  Ajoutez la méthode suivante à la classe `Program` pour définir une feuille de calcul Excel.  
  
     La méthode [Add](http://go.microsoft.com/fwlink/?LinkId=210910) possède un paramètre facultatif pour spécifier un modèle particulier.  Les paramètres optionnels, introduits dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], vous permettent d'omettre l'argument du paramètre, si vous souhaitez utiliser la valeur par défaut de ce dernier.  Dans la mesure où aucun argument n'est envoyé dans le code suivant, `Add` utilise le modèle par défaut et crée un classeur.  L'instruction équivalente dans les versions antérieures de C\# nécessite un argument d'espace réservé : `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-cs[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  À la fin de `DisplayInExcel`, ajoutez le code suivant.  Le code insère les valeurs dans les deux premières colonnes de la première ligne de la feuille de calcul.  
  
     [!code-cs[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]  
  
3.  À la fin de `DisplayInExcel`, ajoutez le code suivant.  La boucle `foreach` place les informations de la liste des comptes dans les deux premières colonnes des lignes successives de la feuille de calcul.  
  
     [!code-cs[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]  
  
4.  À la fin de `DisplayInExcel`, ajoutez le code suivant pour ajuster les largeurs de colonne au contenu.  
  
     [!code-cs[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]  
  
     Les versions antérieures de C\# nécessitent un cast explicite pour ces opérations, parce que `ExcelApp.Columns[1]` retourne un `Object` et que `AutoFit` est une méthode [Range](http://go.microsoft.com/fwlink/?LinkId=210911) Excel.  Les lignes suivantes illustrent le cast.  
  
     [!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
     [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], ainsi que les versions ultérieures, convertit automatiquement l'`Object` retourné en `dynamic` si l'assembly est référencé par l'option du compilateur [\/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) ou si la propriété Excel **Incorporer les types interop** a la valeur true.  La valeur par défaut de cette propriété est true.  
  
### Pour exécuter le projet  
  
1.  À la fin de `Main`, ajoutez la ligne suivante.  
  
     [!code-cs[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]  
  
2.  Appuyez sur CTRL\+F5.  
  
     Une feuille de calcul Excel s'affiche avec les données des deux comptes.  
  
### Pour ajouter un document Word  
  
1.  Pour illustrer d'autres façons grâce auxquelles [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], ainsi que les versions ultérieures, améliore la programmation Office, le code suivant ouvre une application Word et crée une icône liée à la feuille de calcul Excel.  
  
     Collez la méthode `CreateIconInWordDoc`, fournie ultérieurement dans cette étape, dans la classe `Program`.  `CreateIconInWordDoc` utilise les arguments nommés et les arguments facultatifs pour réduire la complexité des appels des méthodes [Add](http://go.microsoft.com/fwlink/?LinkId=210937) et [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099).  Ces appels incorporent deux autres nouvelles fonctionnalités introduites dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], qui simplifient les appels aux méthodes COM comportant des paramètres de référence.  Premièrement, vous pouvez envoyer des arguments aux paramètres de référence comme s'il s'agissait de paramètres de valeur.  Autrement dit, vous pouvez envoyer les valeurs directement, sans créer une variable pour chaque paramètre de référence.  Le compilateur génère des variables temporaires pour stocker les valeurs d'argument et les ignore lors du retour de l'appel.  Ensuite, vous pouvez omettre le mot clé `ref` dans la liste d'arguments.  
  
     La méthode `Add` comporte quatre paramètres de référence, tous facultatifs.  Dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], ou versions ultérieures, vous pouvez omettre les arguments de tout ou partie des paramètres si vous voulez utiliser leur valeur par défaut.  Dans [!INCLUDE[csharp_orcas_long](../../../csharp/programming-guide/interop/includes/csharp-orcas-long-md.md)] et versions antérieures, un argument doit être fourni pour chaque paramètre et l'argument doit être une variable, car les paramètres sont des paramètres de référence.  
  
     La méthode `PasteSpecial` insère le contenu du Presse\-papiers.  La méthode comporte sept paramètres de référence, tous facultatifs.  Le code suivant spécifie des arguments pour deux d'entre eux : `Link` pour créer un lien vers la source du contenu du Presse\-papiers et `DisplayAsIcon` pour afficher le lien sous forme d'icône.  Dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], vous pouvez utiliser des arguments nommés pour ces deux\-là et omettre les autres.  Bien qu'il s'agisse de paramètres de référence, vous n'avez pas à utiliser le mot clé `ref` ou à créer des variables à envoyer tant qu'arguments.  Vous pouvez envoyer les valeurs directement.  Dans [!INCLUDE[csharp_orcas_long](../../../csharp/programming-guide/interop/includes/csharp-orcas-long-md.md)] et versions antérieures, vous devez envoyer un argument de variable pour chaque paramètre de référence.  
  
     [!code-cs[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     Dans [!INCLUDE[csharp_orcas_long](../../../csharp/programming-guide/interop/includes/csharp-orcas-long-md.md)] ou dans les versions antérieures du langage, le code plus complexe suivant est requis.  
  
     [!code-cs[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  À la fin de `Main`, ajoutez l'instruction suivante.  
  
     [!code-cs[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]  
  
3.  À la fin de `DisplayInExcel`, ajoutez l'instruction suivante.  La méthode `Copy` ajoute la feuille de calcul au Presse\-papiers.  
  
     [!code-cs[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]  
  
4.  Appuyez sur CTRL\+F5.  
  
     Un document Word s'affiche avec une icône.  Double\-cliquez sur l'icône pour afficher la feuille de calcul au premier plan.  
  
### Pour définir la propriété Incorporer les types interop  
  
1.  D'autres améliorations sont possibles lorsque vous appelez un type COM qui ne nécessite pas un assembly PIA \(Primary Interop Assembly\) au moment de l'exécution.  La suppression de la dépendance vis\-à\-vis des assemblys PIA aboutit à l'indépendance des versions et facilite le déploiement.  Pour plus d'informations sur les avantages de la programmation sans assemblys PIA, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
     En outre, la programmation est plus facile, car les types qui sont requis et retournés par les méthodes COM peuvent être représentés par l'utilisation du type `dynamic` à la place d'`Object`.  Les variables de type `dynamic` ne sont pas évaluées avant l'exécution, ce qui élimine la nécessité d'un cast explicite.  Pour plus d'informations, consultez [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     Dans [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)], l'incorporation des informations de type au lieu de l'utilisation des assemblys PIA est le comportement par défaut.  En raison de ce comportement par défaut, plusieurs des exemples précédents sont simplifiés, car un cast explicite n'est pas requis.  Par exemple, la déclaration de `worksheet` dans `DisplayInExcel` est écrite sous la forme `Excel._Worksheet workSheet = excelApp.ActiveSheet` plutôt que sous la forme `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.  Les appels à `AutoFit` dans la même méthode nécessiteraient également un cast explicite sans la valeur par défaut, parce que `ExcelApp.Columns[1]` retourne un `Object` et que `AutoFit` est une méthode Excel.  Le code suivant illustre le cast.  
  
     [!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
2.  Pour modifier la valeur par défaut et utiliser les assemblys PIA au lieu d'incorporer les informations de type, développez le nœud **Références** dans l'**Explorateur de solutions**, puis sélectionnez **Microsoft.Office.Interop.Excel** ou **Microsoft.Office.Interop.Word**.  
  
3.  Si la fenêtre **Propriétés** n'apparaît pas, appuyez sur **F4**.  
  
4.  Recherchez **Incorporer les types interop** dans la liste des propriétés et modifiez sa valeur en **False**.  De façon équivalente, vous pouvez compiler à l'aide de l'option du compilateur [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) à la place de l'option [\/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) à l'invite de commandes.  
  
### Pour ajouter une mise en forme supplémentaire au tableau  
  
1.  Remplacez les deux appels à `AutoFit` de `DisplayInExcel` avec l'instruction suivante.  
  
     [!code-cs[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]  
  
     La méthode [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=210948) comporte sept paramètres de valeur, tous facultatifs.  Les arguments nommés et les arguments facultatifs vous permettent de fournir des arguments pour tout ou partie des paramètres, voire pour aucun.  Dans l'instruction précédente, un argument est fourni pour un seul des paramètres, `Format`.  Comme `Format` est le premier paramètre dans la liste des paramètres, vous n'avez pas à fournir le nom du paramètre.  Cependant, l'instruction peut être plus facile à comprendre si le nom du paramètre est inclus, comme illustré dans le code suivant.  
  
     [!code-cs[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]  
  
2.  Appuyez sur CTRL\+F5 pour afficher le résultat.  D'autres formats sont présentés dans l'énumération [XlRangeAutoFormat](http://go.microsoft.com/fwlink/?LinkId=210967).  
  
3.  Comparez l'instruction de l'étape 1 au code suivant, qui indique les arguments requis dans [!INCLUDE[csharp_orcas_long](../../../csharp/programming-guide/interop/includes/csharp-orcas-long-md.md)] ou versions antérieures.  
  
     [!code-cs[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]  
  
## Exemple  
 L'exemple de code suivant illustre l'exemple complet.  
  
 [!code-cs[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## Voir aussi  
 <xref:System.Type.Missing?displayProperty=fullName>   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [Comment : utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)