---
title: "Comment&#160;: convertir des entr&#233;es d&#39;utilisateur num&#233;riques figurant dans des contr&#244;les Web en nombres | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversion (entrée d'utilisateur numérique en nombre)"
  - "mise en forme (.NET Framework), nombres"
  - "mise en forme des nombres (.NET Framework)"
  - "nombres (.NET Framework), conversion (entrée d'utilisateur numérique en nombre)"
  - "chaînes de format numériques (.NET Framework)"
  - "analyser des chaînes (.NET Framework), chaînes numériques"
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: convertir des entr&#233;es d&#39;utilisateur num&#233;riques figurant dans des contr&#244;les Web en nombres
Comme une page Web peut être affichée n'importe où dans le monde, les utilisateurs peuvent entrer des données numériques dans un contrôle <xref:System.Web.UI.WebControls.TextBox> dans un nombre presque illimité de formats.  En conséquence, il est très important de déterminer les paramètres régionaux et la culture de l'utilisateur de la page Web.  Lorsque vous analysez l'entrée d'utilisateur, vous pouvez ensuite appliquer les conventions de mise en forme définies par les paramètres régionaux et la culture de l'utilisateur.  
  
### Pour convertir l'entrée numérique d'un contrôle Web TextBox en un nombre  
  
1.  Déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est rempli.  Si ce n'est pas le cas, passez à l'étape 6.  
  
2.  Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément.  Le premier élément indique la langue et la région par défaut ou préférées de l'utilisateur.  
  
3.  Instanciez un objet <xref:System.Globalization.CultureInfo> qui représente la culture par défaut de l'utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName>.  
  
4.  Appelez la méthode `TryParse` ou `Parse` du type numérique vers lequel vous souhaitez convertir l'entrée de l'utilisateur.  Utilisez une surcharge de la méthode `TryParse` ou `Parse` avec un paramètre `provider` et passez\-lui l'un ou l'autre des éléments suivants :  
  
    -   l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 3 ;  
  
    -   l'objet <xref:System.Globalization.NumberFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.NumberFormat%2A> de l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 3.  
  
5.  Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant du tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6.  Si la conversion échoue encore ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne en utilisant la culture indifférente retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant illustre la page code\-behind complète d'un formulaire Web qui demande à l'utilisateur d'entrer une valeur numérique dans un contrôle <xref:System.Web.UI.WebControls.TextBox> et le convertit en un nombre.  Ce nombre est ensuite doublé et affiché à l'aide des mêmes règles de mise en forme que l'entrée d'origine.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 La propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est remplie à l'aide des noms de culture contenus dans les en\-têtes `Accept-Language` inclus dans une requête HTTP.  Toutefois, certains navigateurs n'incluent pas d'en\-têtes `Accept-Language` dans leurs demandes, et les utilisateurs peuvent également supprimer complètement les en\-têtes.  Il est donc important d'avoir une culture de secours lors de l'analyse de l'entrée d'utilisateur.  En général, la culture de secours est la culture indifférente retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  Comme les utilisateurs peuvent également fournir à Internet Explorer des noms de culture qu'ils entrent dans une zone de texte, il peut arriver que ces noms ne soient pas valides.  Il est donc important d'utiliser la gestion des exceptions lors de l'instanciation d'un objet <xref:System.Globalization.CultureInfo>.  
  
 Lorsqu'il est récupéré d'une requête HTTP soumise par Internet Explorer, le tableau <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est rempli par ordre de préférence de l'utilisateur.  Le premier élément du tableau comporte le nom de la culture\/région principale de l'utilisateur.  Si le tableau contient des éléments supplémentaires, Internet Explorer leur assigne arbitrairement un spécificateur de qualité séparé du nom de culture par un point\-virgule.  Par exemple, une entrée de la culture fr\-FR peut se présenter sous la forme `fr-FR;q=0.7`.  
  
 L'exemple appelle le constructeur <xref:System.Globalization.CultureInfo.%23ctor%2A> avec son paramètre `useUserOverride` défini à `false` pour créer un objet <xref:System.Globalization.CultureInfo>.  Ceci garantit que, si le nom de culture est celui utilisé par défaut sur le serveur, le nouvel objet <xref:System.Globalization.CultureInfo> créé par le constructeur de classe contient les paramètres par défaut d'une culture et ne reflète pas les paramètres substitués à l'aide de l'application **Options régionales et linguistiques** du serveur.  Il est peu probable que les valeurs des paramètres substitués sur le serveur existent sur le système de l'utilisateur ou qu'elles apparaissent dans l'entrée de l'utilisateur.  
  
 Votre code peut appeler la méthode `Parse` ou `TryParse` du type numérique vers lequel l'entrée de l'utilisateur sera convertie.  Il se peut que vous deviez répéter les appels à une méthode d'analyse si vous effectuez une seule opération d'analyse.  Par conséquent, en cas d'échec d'une opération d'analyse, il est préférable d'utiliser la méthode `TryParse`, car elle retourne la valeur `false`.  En revanche, la gestion des exceptions répétées pouvant être levées par la méthode `Parse` risque d'être très onéreuse dans une application Web.  
  
## Compilation du code  
 Pour compiler le code, copiez\-le dans une page code\-behind [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] afin de remplacer tout le code existant.  La page Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] doit contenir les contrôles suivants :  
  
-   un contrôle <xref:System.Web.UI.WebControls.Label> qui n'est pas référencé dans le code  \(affectez la valeur "Enter a Number:" à sa propriété <xref:System.Web.UI.WebControls.TextBox.Text%2A>\) ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `NumericString` ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` \(affectez la valeur "OK" à sa propriété <xref:System.Web.UI.WebControls.Button.Text%2A>\).  
  
 Remplacez le nom de la classe `NumericUserInput` par celui défini par l'attribut `Inherits` de la directive `Page` de la page [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  Remplacez le nom de la référence d'objet `NumericInput` par celui défini par l'attribut `id` de la balise `form` de la page [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
## Sécurité .NET Framework  
 Pour empêcher l'injection de script dans le flux de données HTML, l'entrée d'utilisateur ne doit jamais être répétée directement dans la réponse du serveur,  mais encodée à l'aide de la méthode <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName>.  
  
## Voir aussi  
 [Exécution d'opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)