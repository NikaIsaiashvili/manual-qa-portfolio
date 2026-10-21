# API and SQL Practice

[← Back to portfolio](../README.md)

**Status: planned.** This folder does not contain completed work yet. It corresponds to "Independent QA and Technical Practice" on my CV and LinkedIn.

I have practiced REST API testing with Postman and Swagger, and SQL queries (SELECT, JOIN, GROUP BY) for data checks. That practice was not saved as files I can publish, so this section shows the plan for new exercises. Results will be added here only after I complete them.

## Planned exercises

### REST API testing (Postman)

Target: a public practice API (for example, Restful-Booker or a similar test API).

| # | Exercise | What it checks |
|---|---|---|
| 1 | Send GET, POST, PUT, PATCH, and DELETE requests | Basic CRUD behavior |
| 2 | Add Postman tests for status codes | 200, 201, 400, 401, 403, 404 |
| 3 | Validate JSON response fields and data types | Response structure |
| 4 | Get an auth token and use it in later requests | Authentication flow |
| 5 | Call protected endpoints without a token or with an invalid token | Negative authentication cases |
| 6 | Send missing fields, wrong data types, and boundary values | Input validation |
| 7 | Use environment variables and chain requests | Reusable collections |

**Planned files:** a Postman collection, an environment file without secrets, and a short results table (request, expected, actual, pass/fail). Any problems found will be written up as bug reports in the same format as the [Mini Remittance defect report](../01-mini-remittance/defect-report.md).

### SQL data checks

Target: a small sample database (for example, SQLite with customers, orders, and payments tables).

| # | Exercise | Query type |
|---|---|---|
| 1 | Find orders with a missing or invalid customer | LEFT JOIN, IS NULL |
| 2 | Compare order totals with the sum of order items | JOIN, GROUP BY, SUM |
| 3 | Find duplicate payments for the same order | GROUP BY, HAVING COUNT > 1 |
| 4 | Check values outside allowed ranges (negative amounts, future dates) | WHERE with conditions |
| 5 | Count orders by status | GROUP BY |

**Planned files:** the schema and sample data script, the queries, and the actual output of each query.

---

[← Back to portfolio](../README.md)
