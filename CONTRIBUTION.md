# Getting Started Guide

## Fork the Repository

1.  **Fork the repository** to your GitHub account.
    - Repository: [leremitt_national_bank](https://github.com/leremitt-national-bank/leremitt_national_bank)

## Clone the Forked Repository

2.  **Clone the forked repository** from your GitHub account.

## Add Upstream for GitHub

3.  **Add upstream for GitHub** by using the following command:

    ```bash
    git remote add upstream git@github.com:leremitt-national-bank/leremitt_national_bank.git
    ```

## Choose and Work on Issues

4.  **Comment on the issues** you'd like to work on.
5.  After being **assigned to an issue**, follow these steps:

    - **Checkout** to your main branch:

      ```bash
      git checkout main
      ```

    - **Pull** the latest changes into the main branch from the upstream branch:

      ```bash
      git pull upstream main
      ```

    - **Create a new branch** from the main branch:

      ```bash
      git branch -c <branch-name>#<issueId>
      ```

      - Replace `<branch-name>` with a relevant name and `<issueId>` with the issue ID.

    - **Checkout** to the created branch:

      ```bash
      git checkout <branch-name>#<issueId>
      ```

    - Start working on the issue in this specific branch.
    - After working on the issue, **push the changes** to your forked repo:

      ```bash
      git push origin HEAD
      ```

    - Go to your branch on GitHub and **raise a Pull Request (PR)**.

## Handling Merge Conflicts

- If you encounter any **merge conflicts**, follow these steps:

  - **Checkout** to your main branch:

    ```bash
    git checkout main
    ```

  - **Pull** the latest changes into the main branch from the upstream branch:

    ```bash
    git pull upstream main
    ```

  - **Checkout** to the branch with merge conflicts:

    ```bash
    git checkout <branch-name>#<issueId>
    ```

  - **Merge** the changes from the main branch:

    ```bash
    git merge main
    ```

  - **Resolve** all the merge conflicts, then **push** the changes to the forked repo and **raise a PR** again.

## Final Steps

- After successful review, your PR will be merged.

That's it!

# MySQL Database Setup and Configuration

Follow these steps to set up and configure MySQL database:

### 1. Update Package Repository

```bash
sudo apt update
```

### 2. Install MySQL Server

```bash
sudo apt install mysql-server
```

### 3. Check MySQL Version

```bash
mysql --version
```

### 4. Start MySQL Service

```bash
sudo service mysql start
```

### 5. Access MySQL

```bash
sudo mysql
```

### 6. Show Databases

```sql
SHOW DATABASES;
```

### 7. Create Database

```sql
CREATE DATABASE leremitt;
```

### 8. Use Database

```sql
USE leremitt;
```

### 9. Set SQL Mode and Start Transaction

```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";
```

### 10. Create 'bankdetails' Table

```sql
CREATE TABLE `bankdetails` (
  `email` varchar(100) NOT NULL,
  `accountNumber` varchar(100) DEFAULT NULL,
  `ifscCode` varchar(100) DEFAULT NULL,
  `personName` varchar(100) DEFAULT NULL,
  `timestamp` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

### 11. Create 'usersdata' Table

```sql
CREATE TABLE `usersdata` (
  `email` varchar(255) NOT NULL,
  `personName` varchar(255) DEFAULT NULL,
  `password` varchar(255) DEFAULT NULL,
  `username` varchar(255) DEFAULT NULL,
  `document1` longblob,
  `document2` longblob,
  `document3` longblob,
  `verificationstatus` tinyint(1) DEFAULT NULL,
  `pannumber` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

### 12. Update MySQL User Password

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';
```

### 13. Exit MySQL

```sql
exit
```

Follow these steps to configure MySQL database with the provided schema.
