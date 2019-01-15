# terraform-aws-rds-postgres

Terraform module to create an AWS RDS (Relational Database Server) PostgreSQL.

## Usage
```
module "postgresql" {
  source = "git::https://github.com/felipefrizzo/terraform-aws-rds-postgres?ref=master"

  product_domain = "frizzo"
  service_name   = "rds-master-frizzo"
  environment    = "production"
  description    = "Postgres server to store Github data"

  instance_class = "db.t2.medium"

  allocated_storage = 100

  # Change to valid security group id
  vpc_security_group_ids = [
    "sg-00000000"
  ]

  # Change to valid db subnet group name
  db_subnet_group_name = "rds-subnet-group"

  # Change to valid parameter group name
  parameter_group_name = "default.postgres10.1"

  maintenance_window      = "Sun:02:00-Sun:03:00"
  backup_window           = "00:00-01:00"
  backup_retention_period = 10

  # Change to valid monitoring role arn
  monitoring_role_arn = "arn:aws:iam::000000000000:role/rds-monitoring-role"
}
```