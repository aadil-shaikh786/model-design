# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

<!--- Answer 1 -->
For the bookstore, I propose five main entities: 
- **Employee**: Contains employee information.
    Employee Table - 
                        employee_id (Primary Key)
                        employee_name
                        shift (Morning/Evening)
                        hire_date
- **Order**: Represents orders placed by customers.
    Order Table - 
                    order_id (Primary Key)
                    customer_id (Foreign Key referencing Customer table)
                    employee_id (Foreign Key referencing Employee table)
                    order_date
                    total_amount
- **Sales**: Stores transaction details for each sale.
    Sales Table - 
                    sale_id (Primary Key)
                    order_id (Foreign Key referencing Order table)
                    book_id (Foreign Key referencing Book table)
                    quantity
                    sale_amount
- **Customer**: Maintains customer data.
    Customer Table - 
                        customer_id (Primary Key)
                        customer_name
                        address
- **Book**: Tracks the inventory of books.
    Book Table - 
                    book_id (Primary Key)
                    book_title
                    book_author
                    price
                    stock_quantity

### Relationships:
- Each **Order** is placed by a **Customer**.
- **Sales** are related to **Orders**.
- Each **Book** can appear in multiple **Orders**.
- **Employees** manage **Sales**.

### Date Table:
A **Date** table is added for tracking transactions over time (e.g., sale dates, employee shift schedules).

    Date Table -
                    date_id (Primary Key)
                    date
                    day_of_week
                    month
                    year

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.
<!--- Answer 2 -->
A **Shift** table is added to handle employee schedules, with columns for shift type (morning/evening), employee ID, and dates.
<!--- Answer 2 -->
## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
```
<!--- Answer 3 -->
- **Type 1**: Overwrites customer address when a change occurs.
- **Type 2**: Retains all historical changes by adding a new row for each update.

### Privacy Implications:
Type 2 SCD poses higher privacy risks as it keeps historical customer data, which may not comply with privacy regulations such as GDPR.
<!--- Answer 3 -->
## Question 4
Review the AdventureWorks Schema [here](https://imgur.com/a/u0m8fX6)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
```
Two differences between AdventureWorks ERD and my bookstore ERD:
1. **AdventureWorks has more tables**: It includes extensive entities like suppliers, which my bookstore ERD doesn’t need.
2. **Customer structure**: AdventureWorks separates customer types more granularly, whereas I have a simpler customer table.
# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
