![trivia](https://user-images.githubusercontent.com/73973314/199571591-5b05ac50-9c8b-49cf-8a00-cac57d9f8b3f.PNG)
# API Development and Documentation Project

## Trivia App

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out.

That's where this app comes in! It helped them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application:

1. Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer.
2. Delete questions.
3. Add questions and require that they include question and answer text.
4. Search for questions based on a text query string.
5. Play the quiz game, randomizing either all questions or within a specific category.

This trivia app gave me the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others.

## Initial Set Up

[Fork](https://help.github.com/en/articles/fork-a-repo) the project repository and [clone](https://help.github.com/en/articles/cloning-a-repository) your forked repository to your machine. 

## About the Stack

This is a full stack application. It is designed with key functional areas:

### Backend

The [backend](./backend/README.md) directory contains a completed Flask and SQLAlchemy server. You will work primarily in `__init__.py` to define your endpoints and can reference models.py for DB and SQLAlchemy setup. These are the files need attention in the backend:

1. `backend/flaskr/__init__.py`
2. `backend/test_flaskr.py`

> View the [Backend README](./backend/README.md) for more details.

### Frontend

The [frontend](./frontend/README.md) directory contains a complete React frontend to consume the data from the Flask server. If you have prior experience building a frontend application, you should feel free to edit the endpoints as you see fit for the backend design. If you do not have prior experience building a frontend application, you should read through the frontend code before starting and make notes regarding:

1. What are the end points and HTTP methods the frontend is expecting to consume?
2. How are the requests from the frontend formatted? Are they expecting certain parameters or payloads?

Pay special attention to what data the frontend is expecting from each API response to help guide how you format your API. These are the files you'd want to edit in the frontend:

1. `frontend/src/components/QuestionView.js`
2. `frontend/src/components/FormView.js`
3. `frontend/src/components/QuizView.js`

> View the [Frontend README](./frontend/README.md) for more details.

## API Documentation

## Error Handling
These are the four types of errors the API will return:
*i.* 400 - Bad Request
*ii.* 404 - Not Found
*iii.* 422 - Unprocessable
*iv.* 500 - Internal Server Error

## END POINTS
## POST Request

### POST '/questions'
1. Creates a new question from the react frontend that displays the question and answer, the category of the question and difficulty score.
2. Arguments: None
3. Returns a value and valid ID of the question

### POST '/questions/search'

1. Retrieves question based on search term and returns question based on the search term
2. Arguments: string value
3. Returns object with key questions, total questions, success and current category with their values.
Sample Response:
```
{
    'success': True/False,
    'questions': ['Who is the first programmer?'],
    'total_questions': 10,
    'current_category': 2
}
```

## GET Request

### GET '/questions'
1. Retrieves questions in a paginated way with 10 questions on a page.
2. Arguments: '/questions?page=${this.page}'
3. Returns an object with key questions, total questions, success, current category and  category with their values.
Sample Response:
```
{
    'success': True/False,
    'questions': [{
        'id': 1,
        'question': 'Who is the first Lady programmer?',
        'answer': 'Lady Adalovelace',
        'difficulty': 1,
        'category': 2
    }],
    'total_questions': 10,
    'categories':{
        '1':	'Science',
'2':	'Art'
'3':	'Geography'
'4':	'History'
'5':	'Entertainment'
'6':	'Sports'
    }
    'current_category': 'Science'
}
```

### GET '/categories'
1. Retrieves dictionary of categories with thier ids and the values attached to the category.
2. Arguments: No arguments
3. Returns an object of id: category_string and key: value pairs.
Sample Response: 
```
    'categories':{
        '1':	'Science',
'2':	'Art'
'3':	'Geography'
'4':	'History'
'5':	'Entertainment'
'6':	'Sports'
    }

```
### GET '/quizzes'
1. Retreives the questions
2. Arguments: None
3. Returns any random question which help of random.choice in an object.
Sample Response:
```
    'question':{
        'id':	'3',
'question':	'Who is the first Lady programmer?'
'answer':	'Lady Adalovelace'
'difficulty':	'1'
'category':	'1'

    }

```
### GET '/categories /id/questions'
1. Retreives the questions from the specific category
2. Arguments: integer(id)
3. Returns an object with a key, value contained in the object.
Sample Response:
```
{
'success': true/false,
'question':[{
        'id':	'3',
'question':	'Who is the first Lady programmer?'
'answer':	'Lady Adalovelace'
'difficulty':	'1'
'category':	'1'
},],
'totalQuestions': 10,
'currentCategory': 'Science'
    }

```
### DELETE '/questions/id'
1. Deletes a question by using the question ID
2. Arguments: integer(id)

