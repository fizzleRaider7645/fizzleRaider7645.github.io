---
layout: post
title:      "Bread: A Finance App"
date:       2019-05-21 16:01:05 +0000
permalink:  bread_a_finance_app
---

Bread is a simple accounting app built with React and Rails. The first step was to implement a user login system utilizing Rails’ HttpAuthentication. In short, when a user logs in, params hit the Session controller’s create action. If the user is valid, i.e., their email is present in the database, and their password is correct, the regenerate_auth_token class method (which comes with Rails) is called on the user object. This method generates a random token, which is then stored in a column called auth_token (in the Users table) for that particular user. The newly generated token is then sent to the client with the following json: { token: user.auth_token }.

On the client side, an Auth module checks the token of the incoming json fetch response. If the login credentials are not correct, the token will simply be undefined, and the login process will be halted, and the user will be informed via an alert. If the login is successful, the token will look something like this: 'XrJjoFELfkL6Jphvuk8zEPBd'. This token will then be set by the following function: `sessionStorage.setItem('token', token)`. The first ‘token’ argument is the key, and the second token is the actual string value of the token. In the App component, where the login and log out logic is handled, in this project, the component’s state is then updated to reflect that the user has, or has not been, successfully validated. So long as the users auth_token is held in the browser’s session storage, the user will stay logged in despite refreshes.

After getting the login system to work, I moved on to creating the other main components, which was a bit of a paradigm shift. In previous projects I felt as if UI was more or less a secondary consideration; something you did as a final step to tie up all the hard work you did on the backend.  However, what was interesting about working with React is that user experience comes to fore and presents itself as a facet of the application that immediately requires your attention as a developer. I found the workflow a bit disorienting, however, given how powerful components are, and how quickly you can rework features and layouts, I found my rhythm. 

As for styling, I used material-ui, which had a lot of helpful documentation, and seemed relatively easy to pick up. One major feature I wanted to implement from the outset was some sort of graphing capability. This is a finance-related application, and graphs can really help communicate a lot of important information quickly. I used Chart.js, which also had a lot of helpful documentation. The initial chart feature I wanted to implement was a double bar graph, illustrating the number of deposits and withdrawals a user has actuated over the course of the month. Surprisingly, the most difficult aspect of this was splitting the monthly deposit and withdrawal counts and assigning them to the correct month. After some trial and error, I implemented the following helper function, which did the trick:

```
const transactionMonth = () => {
    return [0,0,0,0,0,0,0,0,0,0,0,0]
}


export const sortChartData = (transactions) => {
    let deposits = [];
    let monthlyWithdrawals = transactionMonth();
    let monthlyDeposits = transactionMonth();
    let withdrawals = [];
    if(transactions.length !== 0) {
        transactions.forEach(transaction => {
            if(transaction.transaction_type === "Deposit") {
                deposits.push(transaction)
            } else {
                withdrawals.push(transaction)
            }
        })
        deposits.forEach(deposit => {
            let month = new Date(deposit.created_at).getMonth()
            monthlyDeposits[month] += 1
        })

        withdrawals.forEach(withdrawal => {
            let month = new Date(withdrawal.created_at).getMonth()
            monthlyWithdrawals[month] += 1
        })
    }
    return {monthlyDeposits, monthlyWithdrawals}
}
```

As for next steps, I would like to add way more functionality to this app. For example, allowing a user to create financial goals, and with those goals, generate charts that graph the user’s successes in achieving those goals. In addition, I would like to add some sort of income calculator that can determine how much money you’ve earned per some criteria, i.e., hourly, monthly, yearly, etc..

