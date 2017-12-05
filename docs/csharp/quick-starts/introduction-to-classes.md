---
title: "Guides de démarrage rapide - Introduction aux classes - Guide C#"
description: "Créez votre premier programme C# et explorez les concepts orientés objet"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: ad6e83d427b55482f9615e0083682bdca6c56704
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-classes"></a><span data-ttu-id="4f70f-103">Introduction aux classes</span><span class="sxs-lookup"><span data-stu-id="4f70f-103">Introduction to classes</span></span>

<span data-ttu-id="4f70f-104">Cette leçon part du principe que vous avez installé le [SDK .NET Core](http://dot.net/core) ainsi qu’un éditeur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="4f70f-104">This lesson assumes that you've installed [.NET Core SDK](http://dot.net/core), and an editor of your choice.</span></span> <span data-ttu-id="4f70f-105">Si vous n’en possédez pas, testez [Visual Studio Code](https://code.visualstudio.com/) ou [Visual Studio](https://www.visualstudio.com/) sur Mac ou Windows.</span><span class="sxs-lookup"><span data-stu-id="4f70f-105">If you don't have one, try [Visual Studio Code](https://code.visualstudio.com/), or [Visual Studio](https://www.visualstudio.com/) on Mac or Windows.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="4f70f-106">Créer une application</span><span class="sxs-lookup"><span data-stu-id="4f70f-106">Create your application</span></span>

<span data-ttu-id="4f70f-107">Dans une fenêtre de terminal, créez un répertoire nommé **classes**.</span><span class="sxs-lookup"><span data-stu-id="4f70f-107">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="4f70f-108">Vous y créerez votre application.</span><span class="sxs-lookup"><span data-stu-id="4f70f-108">You'll build your application there.</span></span> <span data-ttu-id="4f70f-109">Sélectionnez ce répertoire et tapez `dotnet new console` dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="4f70f-109">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="4f70f-110">Cette commande crée votre application.</span><span class="sxs-lookup"><span data-stu-id="4f70f-110">This command creates your application.</span></span> <span data-ttu-id="4f70f-111">Ouvrez **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="4f70f-111">Open **Program.cs**.</span></span> <span data-ttu-id="4f70f-112">Le résultat doit être semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4f70f-112">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="4f70f-113">Dans ce guide de démarrage rapide, vous allez créer des types qui représentent un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="4f70f-113">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="4f70f-114">Les développeurs définissent généralement chaque classe dans un fichier texte différent.</span><span class="sxs-lookup"><span data-stu-id="4f70f-114">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="4f70f-115">Cela simplifie la gestion au fur et à mesure qu’un programme augmente en taille.</span><span class="sxs-lookup"><span data-stu-id="4f70f-115">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="4f70f-116">Créez un fichier nommé **BankAccount.cs** dans le répertoire **classes**.</span><span class="sxs-lookup"><span data-stu-id="4f70f-116">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="4f70f-117">Ce fichier contiendra la définition d’un ***compte bancaire***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-117">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="4f70f-118">La programmation orientée objet organise le code en créant des types sous la forme de ***classes***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-118">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="4f70f-119">Ces classes contiennent le code qui représente une entité spécifique.</span><span class="sxs-lookup"><span data-stu-id="4f70f-119">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="4f70f-120">La classe `BankAccount` représente un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="4f70f-120">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="4f70f-121">Le code implémente des opérations spécifiques à travers des méthodes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="4f70f-121">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="4f70f-122">Dans ce guide de démarrage rapide, le compte bancaire prend en charge le comportement suivant :</span><span class="sxs-lookup"><span data-stu-id="4f70f-122">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="4f70f-123">Il contient un numéro à 10 chiffres qui identifie le compte bancaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="4f70f-123">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="4f70f-124">Il contient une chaîne qui stocke le nom du ou des détenteurs.</span><span class="sxs-lookup"><span data-stu-id="4f70f-124">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="4f70f-125">Le solde peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="4f70f-125">The balance can be retrieved.</span></span>
1. <span data-ttu-id="4f70f-126">Il accepte les dépôts.</span><span class="sxs-lookup"><span data-stu-id="4f70f-126">It accepts deposits.</span></span>
1. <span data-ttu-id="4f70f-127">Il accepte les retraits.</span><span class="sxs-lookup"><span data-stu-id="4f70f-127">It accepts withdrawals.</span></span>
1. <span data-ttu-id="4f70f-128">Le solde initial doit être positif.</span><span class="sxs-lookup"><span data-stu-id="4f70f-128">The initial balance must be positive.</span></span>
1. <span data-ttu-id="4f70f-129">Les retraits ne peuvent pas générer un solde négatif.</span><span class="sxs-lookup"><span data-stu-id="4f70f-129">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="4f70f-130">Définir le type de compte bancaire</span><span class="sxs-lookup"><span data-stu-id="4f70f-130">Define the bank account type</span></span>

<span data-ttu-id="4f70f-131">Vous pouvez commencer par créer les éléments de base d’une classe définissant ce comportement.</span><span class="sxs-lookup"><span data-stu-id="4f70f-131">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="4f70f-132">Le résultat doit être semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4f70f-132">It would look like this:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

<span data-ttu-id="4f70f-133">Avant de poursuivre, examinons ce que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="4f70f-133">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="4f70f-134">La déclaration `namespace` permet d’organiser logiquement votre code.</span><span class="sxs-lookup"><span data-stu-id="4f70f-134">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="4f70f-135">Ce guide de démarrage rapide étant relativement petit, vous allez placer tout le code dans un même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4f70f-135">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="4f70f-136">`public class BankAccount` définit la classe ou le type que vous créez.</span><span class="sxs-lookup"><span data-stu-id="4f70f-136">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="4f70f-137">Tout ce qui est situé entre `{` et `}` après la déclaration de classe définit le comportement de la classe.</span><span class="sxs-lookup"><span data-stu-id="4f70f-137">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="4f70f-138">La classe `BankAccount` a cinq ***membres***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-138">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="4f70f-139">Les trois premiers sont des ***propriétés***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-139">The first three are ***properties***.</span></span> <span data-ttu-id="4f70f-140">Les propriétés sont des éléments de données qui peuvent avoir un code qui applique la validation ou d’autres règles.</span><span class="sxs-lookup"><span data-stu-id="4f70f-140">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="4f70f-141">Les deux derniers sont des ***méthodes***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-141">The last two are ***methods***.</span></span> <span data-ttu-id="4f70f-142">Les méthodes sont des blocs de code qui effectuent une fonction unique.</span><span class="sxs-lookup"><span data-stu-id="4f70f-142">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="4f70f-143">La lecture des noms de chacun des membres doit fournir suffisamment d’informations pour vous permettre (ou à tout autre développeur) de comprendre ce que fait la classe.</span><span class="sxs-lookup"><span data-stu-id="4f70f-143">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="4f70f-144">Ouvrir un nouveau compte</span><span class="sxs-lookup"><span data-stu-id="4f70f-144">Open a new account</span></span>

<span data-ttu-id="4f70f-145">La première fonctionnalité à implémenter est l’ouverture d’un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="4f70f-145">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="4f70f-146">Quand un client ouvre un compte, il doit fournir un solde initial, ainsi que des informations sur le ou les détenteurs du compte.</span><span class="sxs-lookup"><span data-stu-id="4f70f-146">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="4f70f-147">La création d’un objet du type `BankAccount` suppose la définition d’un ***constructeur*** qui assigne ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4f70f-147">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="4f70f-148">Un ***constructeur*** est un membre qui porte le même nom que la classe.</span><span class="sxs-lookup"><span data-stu-id="4f70f-148">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="4f70f-149">Il est utilisé pour initialiser des objets de ce type de classe.</span><span class="sxs-lookup"><span data-stu-id="4f70f-149">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="4f70f-150">Ajoutez le constructeur suivant au type `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="4f70f-150">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="4f70f-151">Les constructeurs sont appelés quand vous créez un objet à l’aide de [`new`](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="4f70f-151">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="4f70f-152">Remplacez la ligne `Console.WriteLine("Hello World!");` dans ***program.cs*** par la ligne suivante (remplacez `<name>` par votre nom) :</span><span class="sxs-lookup"><span data-stu-id="4f70f-152">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="4f70f-153">Tapez `dotnet run` pour observer ce qui se passe.</span><span class="sxs-lookup"><span data-stu-id="4f70f-153">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="4f70f-154">Avez-vous remarqué que le numéro de compte est vide ?</span><span class="sxs-lookup"><span data-stu-id="4f70f-154">Did you notice that the account number is blank?</span></span> <span data-ttu-id="4f70f-155">L’heure est venue de traiter ce point.</span><span class="sxs-lookup"><span data-stu-id="4f70f-155">It's time to fix that.</span></span> <span data-ttu-id="4f70f-156">Le numéro de compte doit être assigné une fois l’objet construit.</span><span class="sxs-lookup"><span data-stu-id="4f70f-156">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="4f70f-157">Mais ce ne devrait pas être à l’appelant de le créer.</span><span class="sxs-lookup"><span data-stu-id="4f70f-157">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="4f70f-158">Le code de la classe `BankAccount` devrait savoir comment assigner de nouveaux numéros de compte.</span><span class="sxs-lookup"><span data-stu-id="4f70f-158">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="4f70f-159">Un moyen simple de le faire consiste à commencer par un numéro à 10 chiffres.</span><span class="sxs-lookup"><span data-stu-id="4f70f-159">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="4f70f-160">Incrémentez-le chaque fois qu’un compte est créé.</span><span class="sxs-lookup"><span data-stu-id="4f70f-160">Increment it when each new account is created.</span></span> <span data-ttu-id="4f70f-161">Enfin, stockez le numéro de compte actuel quand un objet est construit.</span><span class="sxs-lookup"><span data-stu-id="4f70f-161">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="4f70f-162">Ajoutez la déclaration de membre suivante à la classe `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="4f70f-162">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="4f70f-163">Il s’agit d’un membre de données.</span><span class="sxs-lookup"><span data-stu-id="4f70f-163">This is a data member.</span></span> <span data-ttu-id="4f70f-164">Celui-ci est `private`, ce qui signifie qu’il est uniquement accessible par code dans la classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4f70f-164">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="4f70f-165">C’est un moyen de séparer les responsabilités publiques (comme disposer d’un numéro de compte) de l’implémentation privée (c’est-à-dire la façon dont les numéros de compte sont générés). Ajoutez les deux lignes suivantes au constructeur pour assigner le numéro de compte :</span><span class="sxs-lookup"><span data-stu-id="4f70f-165">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="4f70f-166">Tapez `dotnet run` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="4f70f-166">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="4f70f-167">Créer des dépôts et des retraits</span><span class="sxs-lookup"><span data-stu-id="4f70f-167">Create deposits and withdrawals</span></span>

<span data-ttu-id="4f70f-168">La classe de votre compte bancaire doit accepter les dépôts et les retraits pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="4f70f-168">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="4f70f-169">Nous allons implémenter des dépôts et des retraits en créant un journal de chaque transaction du compte.</span><span class="sxs-lookup"><span data-stu-id="4f70f-169">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="4f70f-170">Ce dernier présente plusieurs avantages par rapport à la simple mise à jour du solde à chaque transaction.</span><span class="sxs-lookup"><span data-stu-id="4f70f-170">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="4f70f-171">L’historique peut être utilisé pour auditer toutes les transactions et gérer les soldes au quotidien.</span><span class="sxs-lookup"><span data-stu-id="4f70f-171">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="4f70f-172">En calculant le solde à partir de l’historique de toutes les transactions lorsque nécessaire, toutes les erreurs d’une même transaction qui sont résolues apparaîtront correctement dans le solde dans le calcul suivant.</span><span class="sxs-lookup"><span data-stu-id="4f70f-172">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="4f70f-173">Commençons par créer un type pour représenter une transaction.</span><span class="sxs-lookup"><span data-stu-id="4f70f-173">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="4f70f-174">Il s’agit d’un type simple qui n’a aucune responsabilité.</span><span class="sxs-lookup"><span data-stu-id="4f70f-174">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="4f70f-175">Il a besoin de quelques propriétés.</span><span class="sxs-lookup"><span data-stu-id="4f70f-175">It needs a few properties.</span></span> <span data-ttu-id="4f70f-176">Créez un fichier nommé ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-176">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="4f70f-177">Ajoutez-y le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4f70f-177">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="4f70f-178">Nous allons maintenant ajouter une <xref:System.Collections.Generic.List%601> d’objets `Transaction` à la classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4f70f-178">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="4f70f-179">Ajoutez la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="4f70f-179">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="4f70f-180">Avec la classe <xref:System.Collections.Generic.List%601>, vous devez importer un espace de noms différent.</span><span class="sxs-lookup"><span data-stu-id="4f70f-180">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="4f70f-181">Ajoutez le code suivant au début de **BankAccount.cs** :</span><span class="sxs-lookup"><span data-stu-id="4f70f-181">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="4f70f-182">Nous allons à présent modifier la façon dont le `Balance` est présenté.</span><span class="sxs-lookup"><span data-stu-id="4f70f-182">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="4f70f-183">Il peut être obtenu en additionnant les valeurs de toutes les transactions.</span><span class="sxs-lookup"><span data-stu-id="4f70f-183">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="4f70f-184">Modifiez la déclaration de `Balance` dans la classe `BankAccount` comme suit :</span><span class="sxs-lookup"><span data-stu-id="4f70f-184">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="4f70f-185">Cet exemple montre un aspect important des ***propriétés***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-185">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="4f70f-186">Vous calculez à présent le solde quand un autre programmeur en demande la valeur.</span><span class="sxs-lookup"><span data-stu-id="4f70f-186">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="4f70f-187">Votre calcul énumère toutes les transactions et retourne la somme en tant que solde actuel.</span><span class="sxs-lookup"><span data-stu-id="4f70f-187">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="4f70f-188">Implémentez ensuite les méthodes `MakeDeposit` et `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="4f70f-188">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="4f70f-189">Ces méthodes appliquent les deux règles finales suivantes : le solde initial doit être positif et un retrait ne doit pas générer de solde négatif.</span><span class="sxs-lookup"><span data-stu-id="4f70f-189">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="4f70f-190">Cela introduit le concept d’***exceptions***.</span><span class="sxs-lookup"><span data-stu-id="4f70f-190">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="4f70f-191">Le moyen typique d’indiquer qu’une méthode ne peut pas effectuer correctement son travail consiste à lever une exception.</span><span class="sxs-lookup"><span data-stu-id="4f70f-191">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="4f70f-192">Le type d’exception et le message associé décrivent l’erreur.</span><span class="sxs-lookup"><span data-stu-id="4f70f-192">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="4f70f-193">Ici, la méthode `MakeDeposit` lève une exception si le montant du dépôt est négatif.</span><span class="sxs-lookup"><span data-stu-id="4f70f-193">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="4f70f-194">La méthode `MakeWithdrawal` lève une exception si le montant du retrait est négatif ou si l’application du retrait génère un solde négatif :</span><span class="sxs-lookup"><span data-stu-id="4f70f-194">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="4f70f-195">L’instruction [`throw`](../language-reference/keywords/throw.md) **lève** une exception.</span><span class="sxs-lookup"><span data-stu-id="4f70f-195">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="4f70f-196">L’exécution de la méthode actuelle se termine et reprendra quand un bloc `catch` correspondant sera détecté.</span><span class="sxs-lookup"><span data-stu-id="4f70f-196">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="4f70f-197">Vous ajouterez un bloc `catch` pour tester ce code un peu plus tard.</span><span class="sxs-lookup"><span data-stu-id="4f70f-197">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="4f70f-198">Le constructeur devrait obtenir une modification lui permettant d’ajouter une transaction initiale au lieu de mettre directement le solde à jour.</span><span class="sxs-lookup"><span data-stu-id="4f70f-198">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="4f70f-199">Étant donné que vous avez déjà écrit la méthode `MakeDeposit`, appelez-la à partir de votre constructeur.</span><span class="sxs-lookup"><span data-stu-id="4f70f-199">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="4f70f-200">Le constructeur terminé doit être semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4f70f-200">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="4f70f-201"><xref:System.DateTime.Now?displayProperty=nameWithType> est une propriété qui retourne la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="4f70f-201"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="4f70f-202">Effectuez un essai en ajoutant des dépôts et des retraits dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="4f70f-202">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="4f70f-203">Vérifiez ensuite que vous interceptez bien les conditions d’erreur en essayant de créer un compte avec un solde négatif :</span><span class="sxs-lookup"><span data-stu-id="4f70f-203">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="4f70f-204">Vous utilisez les [instructions `try` et `catch`](../language-reference/keywords/try-catch.md) pour marquer un bloc de code pouvant lever des exceptions et intercepter les erreurs que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="4f70f-204">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="4f70f-205">Vous pouvez utiliser la même technique pour tester le code qui lève une exception de solde négatif :</span><span class="sxs-lookup"><span data-stu-id="4f70f-205">You can use the same technique to test the code that throws for a negative balance:</span></span>

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="4f70f-206">Enregistrez le fichier et tapez `dotnet run` pour effectuer un essai.</span><span class="sxs-lookup"><span data-stu-id="4f70f-206">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="4f70f-207">Test : consigner toutes les transactions</span><span class="sxs-lookup"><span data-stu-id="4f70f-207">Challenge - log all transactions</span></span>

<span data-ttu-id="4f70f-208">Pour terminer ce guide de démarrage rapide, vous pouvez écrire la méthode `GetAccountHistory` qui crée une `string` pour l’historique des transactions.</span><span class="sxs-lookup"><span data-stu-id="4f70f-208">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="4f70f-209">Ajoutez cette méthode au type `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="4f70f-209">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="4f70f-210">Cette méthode utilise la classe <xref:System.Text.StringBuilder> pour mettre en forme une chaîne contenant une ligne par transaction.</span><span class="sxs-lookup"><span data-stu-id="4f70f-210">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="4f70f-211">Vous avez vu le code de mise en forme de chaîne précédemment dans ces guides de démarrage rapide.</span><span class="sxs-lookup"><span data-stu-id="4f70f-211">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="4f70f-212">Vous pouvez observer le nouveau caractère `\t`.</span><span class="sxs-lookup"><span data-stu-id="4f70f-212">One new character is `\t`.</span></span> <span data-ttu-id="4f70f-213">Celui-ci insère une tabulation pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="4f70f-213">That inserts a tab to format the output.</span></span>

<span data-ttu-id="4f70f-214">Ajoutez cette ligne pour effectuer un essai dans **Program.cs** :</span><span class="sxs-lookup"><span data-stu-id="4f70f-214">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="4f70f-215">Tapez `dotnet run` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="4f70f-215">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f70f-216">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4f70f-216">Next Steps</span></span>

<span data-ttu-id="4f70f-217">Si vous êtes bloqué, vous pouvez afficher la source de ce guide de démarrage rapide [dans notre dépôt GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/).</span><span class="sxs-lookup"><span data-stu-id="4f70f-217">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="4f70f-218">Félicitations, vous avez terminé tous nos guides de démarrage rapide.</span><span class="sxs-lookup"><span data-stu-id="4f70f-218">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="4f70f-219">Si vous souhaitez en savoir plus, explorez nos [didacticiels](../tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f70f-219">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
