```json
{
  "status": "success",
  "result": {
    "optimization_analysis": {
      "common_performance_issues": [
        "Missing or inefficient indexes",
        "N+1 query problems",
        "Unnecessary data fetching",
        "Lack of query result caching",
        "Inefficient JOIN operations",
        "Missing database connection pooling"
      ],
      "recommended_optimizations": {
        "indexing_strategy": {
          "primary_recommendations": [
            "Create composite indexes for frequently queried column combinations",
            "Add indexes on foreign key columns",
            "Implement partial indexes for filtered queries",
            "Remove unused or redundant indexes"
          ],
          "monitoring_tools": ["EXPLAIN ANALYZE", "Database query logs", "Performance monitoring dashboards"]
        },
        "query_optimization": {
          "techniques": [
            "Use SELECT with specific columns instead of SELECT *",
            "Implement pagination for large result sets",
            "Optimize WHERE clause conditions",
            "Use EXISTS instead of IN for subqueries where appropriate",
            "Batch INSERT/UPDATE operations"
          ],
          "caching_strategies": [
            "Implement query result caching with Redis/Memcached",
            "Use database-level query caching",
            "Application-level caching for frequently accessed data"
          ]
        },
        "connection_management": {
          "recommendations": [
            "Implement connection pooling (e.g., pgBouncer for PostgreSQL)",
            "Optimize connection pool size based on application load",
            "Use read replicas for read-heavy workloads",
            "Implement database load balancing"
          ]
        },
        "schema_optimization": {
          "best_practices": [
            "Normalize database schema appropriately",
            "Use appropriate data types to minimize storage",
            "Implement table partitioning for large tables",
            "Archive old data to reduce table sizes"
          ]
        }
      },
      "implementation_plan": {
        "phase_1_immediate": [
          "Audit existing queries using EXPLAIN ANALYZE",
          "Identify slow queries from database logs",
          "Add missing indexes on frequently queried columns"
        ],
        "phase_2_optimization": [
          "Implement query result caching",
          "Optimize N+1 query patterns",
          "Set up connection pooling"
        ],
        "phase_3_monitoring": [
          "Implement performance monitoring",
          "Set up alerting for slow queries",
          "Regular performance review cycles"
        ]
      },
      "performance_metrics": {
        "key_indicators": [
          "Query execution time",
          "Database CPU utilization",
          "Connection pool usage",
          "Cache hit ratios",
          "Slow query frequency"
        ],
        "target_improvements": {
          "query_response_time": "Reduce by 60-80%",
          "database_cpu_usage": "Reduce by 40-60%",
          "concurrent_connections": "Optimize for 2-3x current load"
        }
      }
    },
    "code_examples": {
      "indexing": "CREATE INDEX CONCURRENTLY idx_users_email_active ON users(email, is_active) WHERE is_active = true;",
      "query_optimization": "SELECT u.id, u.name, p.title FROM users u JOIN posts p ON u.id = p.user_id WHERE u.is_active = true LIMIT 20 OFFSET 0;",
      "caching": "// Implement Redis caching layer\nconst cachedResult = await redis.get(cacheKey);\nif (!cachedResult) {\n  const result = await database.query(sql);\n  await redis.setex(cacheKey, 300, JSON.stringify(result));\n  return result;\n}"
    }
  },
  "summary": "Analyzed database query performance optimization strategies including indexing, query optimization, caching, and connection management. Provided a comprehensive implementation plan with specific recommendations for immediate improvements and long-term performance gains.",
  "confidence": 92
}
```