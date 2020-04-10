# terraform-aws-postgresql-single-rds

Copy of [terraform-aws-postgresql-rds](https://github.com/OneCloudInc/terraform-aws-postgresql-rds) but modified for single rds creation instead of multiple

## Usage

```javascript
module "postgresql_rds" {
  source = "github.com/OneCloudInc/terraform-aws-postgresql-single-rds"
  vpc_id = "vpc-123456"
  vpc_security_group_ids = ["sg-1", "sg-2"]
  allocated_storage = "32"
  engine_version = "12.2"
  instance_type = "db.t2.micro"
  storage_type = "gp2"
  database_identifier = "really-c00l-database"
  database_name = "onecloud_staging"
  database_username = "onecloud"
  database_password = "hunter2"
  database_port = "5432"
  backup_retention_period = "30"
  backup_window = "04:00-04:30"
  maintenance_window = "sun:04:30-sun:05:30"
  auto_minor_version_upgrade = false
  multi_availability_zone = true
  storage_encrypted = false
  subnet_group = "${aws_db_subnet_group.default.name}"
  parameter_group = "${aws_db_parameter_group.default.name}"

  alarm_cpu_threshold = "75"
  alarm_disk_queue_threshold = "10"
  alarm_free_disk_threshold = "5000000000"
  alarm_free_memory_threshold = "128000000"
  alarm_actions = ["arn:aws:sns..."]

  project = "Something"
  environment = "Staging"
}
```
