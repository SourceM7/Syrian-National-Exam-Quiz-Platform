# Quiz Application

A Laravel API quiz platform for creating and managing interactive quizzes.

## Installation

### Standard Installation

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/quiz-app.git
   cd quiz-app
   ```

2. Install dependencies
   ```bash
   composer install
   ```

3. Create and configure your environment file
   ```bash
   cp .env.example .env
   ```

4. Generate application key
   ```bash
   php artisan key:generate
   ```

5. Configure your database connection in the `.env` file
   ```
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=laravel
   DB_USERNAME=root
   DB_PASSWORD=root
   ```

6. Run database migrations and seed
   ```bash
   php artisan migrate --seed
   ```
 
7. Start the development server
   ```bash
   php artisan serve
   ```

### Docker Installation

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/quiz-app.git
   cd quiz-app
   ```

2. Create and configure your environment file
   ```bash
   cp .env.example .env
   ```

3. Build and start the containers
   ```bash
   docker-compose up -d
   ```

4. Install dependencies
   ```bash
   docker-compose exec app composer install
   ```

5. Generate application key
   ```bash
   docker-compose exec app php artisan key:generate
   ```

6. Run database migrations and seed
   ```bash
   docker-compose exec app php artisan migrate --seed
   ```

7. Set proper permissions
   ```bash
   docker-compose exec app chown -R www-data:www-data storage bootstrap/cache
   ```



## API Routes

All routes are prefixed with `/api/Darrebni`

### Authentication Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /auth/register | Register a new user |
| POST | /auth/login | User login |
| POST | /auth/UserProfile/logout | User logout (authenticated) |

### Public Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /Slider/all | Get all sliders |
| GET | /Collages/all | Get all colleges |
| GET | /Specialization/allSpecialization | Get all specializations |
| GET | /Collages/getSpecialization/collage={id} | Get specializations by college ID |
| GET | /Collages/Specializations | Get colleges with specializations |
| POST | /Specialization/search | Search by specialization |

### Authenticated Routes

#### User & Profile

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /UserProfile/Info | Get user information |
| PUT | /UserProfile/update | Update user profile |
| DELETE | /UserProfile/delete | Delete user profile |
| POST | /UserProfile/Feedback | Submit feedback |
| GET | /Notification/getall | Get all notifications |
| GET | /aboutus/get | Get about us information |

#### Terms & Subjects

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /terms/specialization/{id}/getall | Get terms by specialization |
| GET | /terms/getall | Get all terms |
| GET | /Terms/Filters/subj/{id} | Filter terms by subject |
| GET | /Terms/Filters/spec/{id} | Filter terms by specialization |
| GET | /Specialization/checkButtons | Check buttons availability |
| GET | /Specialization/filters/type/{type} | Show master/graduation subjects |
| GET | /Specialization/filters/specialization/{id} | Show subjects by specialization |

#### Questions & Answers

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /Question/single/{id} | Get single question |
| GET | /Questions/Terms/term_id/{termid}/Subjects/subject_id/{id} | Get questions by term and subject |
| GET | /Terms/Question/term_id/{id} | Show questions for a term |
| GET | /Terms/{term}/nextQuestion/{question} | Get next question in term |
| GET | /Terms/{term}/prevQuestion/{question} | Get previous question in term |
| GET | /Terms/Filters/question/{id} | Get questions by term ID |
| GET | /Books/Questions/Subject/{id} | Get book questions by subject |
| GET | /Books/Question/sub_id/{id} | Show questions for books |
| GET | /Books/{subid}/nextQuestion/{question} | Get next question in a book |
| GET | /Books/{subid}/prevQuestion/{question} | Get previous question in a book |
| GET | /BankQuestions/specialization/{id} | Get bank questions by specialization |
| GET | /SpecializationTermsQuestions/term/{id} | Get questions for specialization term |

#### Important Questions

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /ImportanceQuestions/addQuestion/question/{id} | Mark question as important |
| GET | /ImportanceQuestions/getImportances | Get important questions |
| DELETE | /ImportanceQuestions/remove/question/{id} | Remove from important |

### Admin Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /dashboard/Notification/send | Send notification |
| POST | /dashboard/Notification/update | Update token |
| POST | /dashboard/Slider/create | Create slider |
| PUT | /dashboard/Slider/update/{id} | Update slider |
| DELETE | /dashboard/Slider/delete/{id} | Delete slider |
| POST | /dashboard/Specialization/create | Create specialization |
| PUT | /dashboard/Specialization/update/{id} | Update specialization |
| DELETE | /dashboard/Specialization/delete/{id} | Delete specialization |
| POST | /dashboard/Subject/create | Create subject |
| PUT | /dashboard/Subject/update/{id} | Update subject |
| DELETE | /dashboard/Subject/delete/{id} | Delete subject |
| POST | /dashboard/Term/store | Create term |
| PUT | /dashboard/Term/update/{id} | Update term |
| DELETE | /dashboard/Term/delete/{id} | Delete term |
| POST | /dashboard/Question/create | Create question |
| PUT | /dashboard/Question/update/{id} | Update question |
| DELETE | /dashboard/Question/delete/{id} | Delete question |
| POST | /dashboard/Answer/store | Create answer |
| PUT | /dashboard/Answer/update/{id} | Update answer |
| DELETE | /dashboard/Answer/delete/{id} | Delete answer |

## Development

### Running Commands

When using Docker, prefix Laravel commands with `docker-compose exec app`:

```bash
# Run migrations
docker-compose exec app php artisan migrate

# Clear cache
docker-compose exec app php artisan cache:clear
```
 
## Stopping the Application

```bash
# When using Docker
docker-compose down

# To remove volumes as well
docker-compose down -v
```
