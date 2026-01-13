<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Freestore - Бесплатная платформа для игр</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #0d1b2a;
            --secondary: #1b3a4b;
            --accent: #2a9d8f;
            --light: #e0e1dd;
            --dark: #0a141e;
            --success: #4caf50;
            --warning: #ff9800;
            --danger: #f44336;
            --admin: #e63946;
            --highlight: #ffd166;
        }

        body {
            background-color: var(--primary);
            color: var(--light);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background-color: var(--dark);
            padding: 15px 0;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.4);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo i {
            font-size: 2.5rem;
            color: var(--accent);
        }

        .logo h1 {
            font-size: 1.8rem;
            font-weight: 800;
            color: white;
            background: linear-gradient(90deg, var(--accent), var(--highlight));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .logo span {
            color: var(--accent);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            font-size: 1.1rem;
            padding: 8px 12px;
            border-radius: 4px;
        }

        nav a:hover {
            color: var(--accent);
            background-color: rgba(42, 157, 143, 0.1);
        }

        .user-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .user-actions i {
            font-size: 1.5rem;
            color: var(--light);
            cursor: pointer;
            transition: color 0.3s;
            padding: 8px;
            border-radius: 50%;
        }

        .user-actions i:hover {
            color: var(--accent);
            background-color: rgba(42, 157, 143, 0.1);
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 10px;
            background-color: var(--secondary);
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .user-profile:hover {
            background-color: #234a5c;
        }

        .user-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background-color: var(--accent);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            background-size: cover;
            background-position: center;
        }

        .admin-badge {
            background-color: var(--admin);
            color: white;
            padding: 2px 8px;
            border-radius: 10px;
            font-size: 0.7rem;
            margin-left: 5px;
        }

        /* Search bar */
        .search-container {
            position: relative;
            display: flex;
            align-items: center;
        }

        #search-input {
            padding: 10px 15px;
            padding-right: 40px;
            background-color: var(--secondary);
            border: 1px solid #3d4c5e;
            border-radius: 20px;
            color: var(--light);
            font-size: 1rem;
            width: 250px;
            transition: width 0.3s;
        }

        #search-input:focus {
            width: 300px;
            outline: none;
            border-color: var(--accent);
        }

        #search-btn {
            position: absolute;
            right: 10px;
            background: none;
            border: none;
            color: var(--light);
            cursor: pointer;
        }

        /* Hero section */
        .hero {
            background: linear-gradient(rgba(10, 20, 30, 0.9), rgba(10, 20, 30, 0.9)), url('https://images.unsplash.com/photo-1550745165-9bc0b252726f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            padding: 80px 0;
            text-align: center;
            margin-bottom: 40px;
        }

        .hero h2 {
            font-size: 3rem;
            margin-bottom: 20px;
            color: white;
            background: linear-gradient(90deg, var(--accent), var(--highlight));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 30px;
            color: var(--light);
        }

        .cta-button {
            display: inline-block;
            background-color: var(--accent);
            color: white;
            padding: 15px 30px;
            border-radius: 4px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            transition: background-color 0.3s, transform 0.2s;
            border: none;
            cursor: pointer;
        }

        .cta-button:hover {
            background-color: #21867a;
            transform: translateY(-3px);
        }

        /* Main content */
        main {
            padding: 40px 0;
        }

        .section-title {
            font-size: 2rem;
            margin-bottom: 30px;
            color: white;
            border-left: 4px solid var(--accent);
            padding-left: 15px;
        }

        .section-title.admin {
            border-left-color: var(--admin);
        }

        /* Tabs */
        .tabs {
            display: flex;
            margin-bottom: 30px;
            border-bottom: 2px solid var(--secondary);
            flex-wrap: wrap;
        }

        .tab {
            padding: 12px 25px;
            background: none;
            border: none;
            color: var(--light);
            font-size: 1.1rem;
            cursor: pointer;
            position: relative;
            transition: color 0.3s;
        }

        .tab:hover {
            color: var(--accent);
        }

        .tab.active {
            color: var(--accent);
            font-weight: bold;
        }

        .tab.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--accent);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        /* Games grid */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }

        .game-card {
            background-color: var(--secondary);
            border-radius: 8px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
            border: 1px solid transparent;
        }

        .game-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.3);
            border-color: var(--accent);
        }

        .game-image {
            height: 160px;
            background-color: #000;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: var(--accent);
            background-size: cover;
            background-position: center;
            position: relative;
        }

        .game-status {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: rgba(0,0,0,0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
        }

        .game-status.pending {
            background-color: var(--warning);
        }

        .game-status.approved {
            background-color: var(--success);
        }

        .game-status.rejected {
            background-color: var(--danger);
        }

        .game-info {
            padding: 20px;
            position: relative;
        }

        .game-title {
            font-size: 1.3rem;
            margin-bottom: 10px;
            color: white;
        }

        .game-description {
            font-size: 0.95rem;
            color: #a3b8c6;
            margin-bottom: 20px;
            height: 60px;
            overflow: hidden;
        }

        .game-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            font-size: 0.9rem;
        }

        .game-author {
            color: var(--accent);
        }

        .game-rating {
            color: var(--highlight);
        }

        .game-actions {
            display: flex;
            justify-content: space-between;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border-radius: 4px;
            border: none;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn:hover {
            transform: translateY(-2px);
        }

        .btn-download {
            background-color: var(--accent);
            color: white;
            flex-grow: 1;
        }

        .btn-download:hover {
            background-color: #21867a;
        }

        .btn-play {
            background-color: var(--highlight);
            color: var(--dark);
            flex-grow: 1;
        }

        .btn-play:hover {
            background-color: #ffc145;
        }

        .btn-details {
            background-color: transparent;
            color: var(--light);
            border: 1px solid var(--light);
        }

        .btn-details:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .btn-admin {
            background-color: var(--admin);
            color: white;
            margin: 5px;
        }

        .btn-admin:hover {
            background-color: #d32f2f;
        }

        /* Upload section */
        .upload-section {
            background-color: var(--secondary);
            border-radius: 8px;
            padding: 40px;
            margin-bottom: 60px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
            border: 1px solid var(--accent);
        }

        .upload-form {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .form-group label {
            font-weight: bold;
            color: white;
        }

        .form-group input, .form-group textarea, .form-group select {
            padding: 12px 15px;
            background-color: var(--primary);
            border: 1px solid #3d4c5e;
            border-radius: 4px;
            color: var(--light);
            font-size: 1rem;
        }

        .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
            outline: none;
            border-color: var(--accent);
        }

        .form-group textarea {
            min-height: 120px;
            resize: vertical;
        }

        .file-upload {
            border: 2px dashed #3d4c5e;
            padding: 30px;
            text-align: center;
            border-radius: 4px;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .file-upload:hover {
            border-color: var(--accent);
        }

        .file-upload i {
            font-size: 3rem;
            color: var(--accent);
            margin-bottom: 15px;
        }

        .file-upload p {
            color: #a3b8c6;
        }

        .btn-upload {
            background-color: var(--accent);
            color: white;
            padding: 15px;
            font-size: 1.1rem;
            font-weight: bold;
            align-self: flex-start;
        }

        .btn-upload:hover {
            background-color: #21867a;
        }

        /* Profile section */
        .profile-section {
            background-color: var(--secondary);
            border-radius: 8px;
            padding: 40px;
            margin-bottom: 60px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
        }

        .profile-header {
            display: flex;
            align-items: center;
            gap: 30px;
            margin-bottom: 40px;
        }

        .profile-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background-color: var(--accent);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            font-weight: bold;
            background-size: cover;
            background-position: center;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            border: 3px solid var(--accent);
        }

        .profile-avatar:hover::after {
            content: 'Изменить';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1rem;
        }

        .profile-info h2 {
            font-size: 2rem;
            margin-bottom: 10px;
            color: white;
        }

        .profile-info p {
            color: #a3b8c6;
            max-width: 600px;
        }

        /* Reviews */
        .reviews-section {
            margin-top: 40px;
        }

        .review-form {
            background-color: var(--primary);
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 30px;
            border: 1px solid var(--secondary);
        }

        .review-form textarea {
            width: 100%;
            min-height: 100px;
            margin-bottom: 15px;
            padding: 12px;
            background-color: var(--secondary);
            border: 1px solid #3d4c5e;
            border-radius: 4px;
            color: var(--light);
            font-size: 1rem;
        }

        .review {
            background-color: var(--primary);
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 3px solid var(--accent);
        }

        .review-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }

        .review-author {
            font-weight: bold;
            color: var(--accent);
        }

        .review-rating {
            color: var(--highlight);
        }

        /* Auth modals */
        .auth-modal, .profile-modal, .support-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .auth-content, .profile-content, .support-content {
            background-color: var(--secondary);
            border-radius: 8px;
            width: 90%;
            max-width: 500px;
            padding: 40px;
            position: relative;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }

        .auth-tabs {
            display: flex;
            margin-bottom: 30px;
        }

        .auth-tab {
            flex: 1;
            padding: 15px;
            background: none;
            border: none;
            color: var(--light);
            font-size: 1.1rem;
            cursor: pointer;
            border-bottom: 2px solid var(--secondary);
        }

        .auth-tab.active {
            color: var(--accent);
            border-bottom-color: var(--accent);
        }

        .auth-form {
            display: none;
        }

        .auth-form.active {
            display: block;
        }

        .terms {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 20px 0;
        }

        .terms input {
            width: 20px;
            height: 20px;
        }

        .close-auth, .close-profile, .close-support {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.8rem;
            color: var(--light);
            cursor: pointer;
            transition: color 0.3s;
        }

        .close-auth:hover, .close-profile:hover, .close-support:hover {
            color: var(--accent);
        }

        /* Support chat */
        .chat-container {
            max-height: 400px;
            overflow-y: auto;
            margin-bottom: 20px;
            padding: 10px;
            background-color: var(--primary);
            border-radius: 8px;
        }

        .chat-message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 15px;
            max-width: 80%;
        }

        .chat-message.bot {
            background-color: var(--accent);
            color: white;
            align-self: flex-start;
            margin-right: auto;
        }

        .chat-message.user {
            background-color: var(--highlight);
            color: var(--dark);
            align-self: flex-end;
            margin-left: auto;
        }

        .chat-input-container {
            display: flex;
            gap: 10px;
        }

        #chat-input {
            flex-grow: 1;
            padding: 12px;
            background-color: var(--primary);
            border: 1px solid #3d4c5e;
            border-radius: 20px;
            color: var(--light);
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            padding: 40px 0 20px;
            margin-top: 40px;
        }

        .footer-content {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 40px;
            margin-bottom: 30px;
        }

        .footer-column {
            flex: 1;
            min-width: 250px;
        }

        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            color: white;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column li {
            margin-bottom: 10px;
        }

        .footer-column a {
            color: #a3b8c6;
            text-decoration: none;
            trans
