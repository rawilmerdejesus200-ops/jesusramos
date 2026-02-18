<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jesús Ramos - Frases</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            color: #fff;
            overflow-x: hidden;
        }

        .logo-container {
            text-align: center;
            padding: 40px 20px;
        }

        .logo {
            display: inline-block;
            position: relative;
        }

        .logo-text {
            font-size: 3rem;
            font-weight: 900;
            background: linear-gradient(45deg, #e94560, #ff6b6b, #feca57);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
            letter-spacing: 3px;
        }

        .logo-subtitle {
            font-size: 1rem;
            color: #a0a0a0;
            margin-top: 10px;
            letter-spacing: 5px;
            text-transform: uppercase;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }

        .quote-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .quote-text {
            font-size: 1.5rem;
            line-height: 1.8;
            color: #fff;
            font-style: italic;
            margin-bottom: 20px;
        }

        .quote-author {
            color: #e94560;
            font-size: 1rem;
            font-weight: 600;
        }

        .btn-container {
            text-align: center;
            margin: 40px 0;
        }

        .btn {
            background: linear-gradient(45deg, #e94560, #ff6b6b);
            border: none;
            padding: 15px 40px;
            font-size: 1.1rem;
            color: #fff;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(233, 69, 96, 0.4);
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 600;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(233, 69, 96, 0.6);
        }

        .btn:active {
            transform: translateY(0);
        }

        .counter {
            text-align: center;
            color: #a0a0a0;
            font-size: 0.9rem;
            margin-top: 20px;
        }

        @media (max-width: 600px) {
            .logo-text { font-size: 2rem; }
            .quote-text { font-size: 1.2rem; }
            .quote-card { padding: 25px; }
        }
    </style>
</head>
<body>
    <div class="logo-container">
        <div class="logo">
            <div class="logo-text">Jesús Ramos</div>
            <div class="logo-subtitle">Frases & Reflexiones</div>
        </div>
    </div>

    <div class="container">
        <div class="quote-card">
            <div class="quote-text" id="quoteText">"La vida es lo que pasa mientras estás ocupado haciendo otros planes."</div>
            <div class="quote-author" id="quoteAuthor">— John Lennon</div>
        </div>

        <div class="btn-container">
            <button class="btn" onclick="newQuote()">Nueva Frase</button>
        </div>

        <div class="counter" id="counter">Frase 1 de 100</div>
    </div>

    <script>
        const quotes = [
            { text: "La vida es lo que pasa mientras estás ocupado haciendo otros planes.", author: "John Lennon" },
            { text: "El único modo de hacer un gran trabajo es amar lo que haces.", author: "Steve Jobs" },
            { text: "No cuentes los días, haz que los días cuenten.", author: "Muhammad Ali" },
            { text: "La mejor venganza es un éxito masivo.", author: "Frank Sinatra" },
            { text: "Todo lo que puedas imaginar es real.", author: "Pablo Picasso" },
            { text: "Sé el cambio que quieres ver en el mundo.", author: "Mahatma Gandhi" },
            { text: "No hay atajos para cualquier lugar que valga la pena ir.", author: "Beverly Sills" },
            { text: "La felicidad no es algo hecho. Viene de tus propias acciones.", author: "Dalai Lama" },
            { text: "Si puedes soñarlo, puedes hacerlo.", author: "Walt Disney" },
            { text: "El fracaso es el condimento que le da sabor al éxito.", author: "Truman Capote" },
            { text: "No dejes que el ruido de las opiniones de otros apague tu propia voz interior.", author: "Steve Jobs" },
            { text: "La vida es 10% lo que te sucede y 90% cómo reaccionas ante ello.", author: "Charles R. Swindoll" },
            { text: "El éxito no es definitivo, el fracaso no es fatal: lo que cuenta es el valor para continuar.", author: "Winston Churchill" },
            { text: "No importa cuán lento vayas, siempre y cuando no te detengas.", author: "Confucio" },
            { text: "Todo parece imposible hasta que se hace.", author: "Nelson Mandela" },
            { text: "El futuro pertenece a quienes creen en la belleza de sus sueños.", author: "Eleanor Roosevelt" },
            { text: "No esperes. El momento nunca será el ideal.", author: "Napoleón Hill" },
            { text: "El único límite a nuestros logros de mañana son nuestras dudas de hoy.", author: "Franklin D. Roosevelt" },
            { text: "Haz lo que puedas, con lo que tengas, donde estés.", author: "Theodore Roosevelt" },
            { text: "Cree que puedes y ya estás a mitad de camino.", author: "Theodore Roosevelt" },
            { text: "La educación es el arma más poderosa que puedes usar para cambiar el mundo.", author: "Nelson Mandela" },
            { text: "La mente es todo. Lo que piensas, te conviertes.", author: "Buda" },
            { text: "No hay viento favorable para el que no sabe a qué puerto se dirige.", author: "Séneca" },
            { text: "La vida no se trata de encontrarte a ti mismo, sino de crearte a ti mismo.", author: "George Bernard Shaw" },
            { text: "El mejor momento para plantar un árbol fue hace 20 años. El segundo mejor momento es ahora.", author: "Proverbio chino" },
            { text: "Tu tiempo es limitado, no lo desperdicies viviendo la vida de otro.", author: "Steve Jobs" },
            { text: "La simplicidad es la máxima sofisticación.", author: "Leonardo da Vinci" },
            { text: "Lo que no te mata te hace más fuerte.", author: "Friedrich Nietzsche" },
            { text: "La paciencia es amarga, pero su fruto es dulce.", author: "Jean-Jacques Rousseau" },
            { text: "El conocimiento es poder.", author: "Francis Bacon" },
            { text: "La imaginación es más importante que el conocimiento.", author: "Albert Einstein" },
            { text: "No puedes cruzar el mar simplemente mirando el agua.", author: "Rabindranath Tagore" },
            { text: "El que tiene un porqué para vivir puede soportar casi cualquier cómo.", author: "Friedrich Nietzsche" },
            { text: "La vida es realmente simple, pero insistimos en hacerla complicada.", author: "Confucio" },
            { text: "El éxito es la suma de pequeños esfuerzos repetidos día tras día.", author: "Robert Collier" },
            { text: "No juzgues cada día por la cosecha que recoges, sino por las semillas que plantas.", author: "Robert Louis Stevenson" },
            { text: "El único lugar donde el éxito viene antes que el trabajo es en el diccionario.", author: "Vidal Sassoon" },
            { text: "No importa cuántas veces fracases, solo debes acertar una vez.", author: "Mark Cuban" },
            { text: "Los obstáculos son esas cosas atemorizantes que ves cuando apartas los ojos de tu meta.", author: "Henry Ford" },
            { text: "La acción es la clave fundamental para todo éxito.", author: "Pablo Picasso" },
            { text: "No sueñes tu vida, vive tu sueño.", author: "Anónimo" },
            { text: "El secreto del éxito es la constancia del propósito.", author: "Benjamin Disraeli" },
            { text: "El éxito es ir de fracaso en fracaso sin perder el entusiasmo.", author: "Winston Churchill" },
            { text: "No encuentres la falta, encuentra el remedio.", author: "Henry Ford" },
            { text: "El éxito no es para los débiles de corazón.", author: "Anónimo" },
            { text: "La motivación te pone en marcha, el hábito te mantiene en movimiento.", author: "Jim Ryun" },
            { text: "No dejes que lo que no puedes hacer interfiera con lo que puedes hacer.", author: "John Wooden" },
            { text: "El éxito es la mejor venganza.", author: "Anónimo" },
            { text: "Trabaja duro en silencio, deja que tu éxito haga el ruido.", author: "Frank Ocean" },
            { text: "Los ganadores nunca se rinden y los que se rinden nunca ganan.", author: "Vince Lombardi" },
            { text: "El éxito no es accidente. Es trabajo duro, perseverancia, aprendizaje, estudio, sacrificio y amor por lo que haces.", author: "Pelé" },
            { text: "El dolor que sientes hoy es la fuerza que sentirás mañana.", author: "Anónimo" },
            { text: "Nunca es demasiado tarde para ser lo que podrías haber sido.", author: "George Eliot" },
            { text: "La disciplina es el puente entre metas y logros.", author: "Jim Rohn" },
            { text: "No busques el momento perfecto, solo busca el momento y hazlo perfecto.", author: "Anónimo" },
            { text: "No te preocupes por los fracasos, preocúpate por las oportunidades que pierdes cuando ni siquiera lo intentas.", author: "Jack Canfield" },
            { text: "El éxito es aprender a ir de fracaso en fracaso sin perder el entusiasmo.", author: "Winston Churchill" },
            { text: "La vida es como montar en bicicleta. Para mantener el equilibrio debes seguir moviéndote.", author: "Albert Einstein" },
            { text: "No hay ascensor hacia el éxito. Tienes que subir las escaleras.", author: "Anónimo" },
            { text: "El éxito no es la clave de la felicidad. La felicidad es la clave del éxito.", author: "Albert Schweitzer" },
            { text: "No dejes que la opinión de alguien más se convierta en tu realidad.", author: "Les Brown" },
            { text: "La vida es corta. Sonríe mientras aún tienes dientes.", author: "Anónimo" },
            { text: "No importa cuántas veces caigas, importa cuántas veces te levantes.", author: "Anónimo" },
            { text: "La mejor manera de predecir el futuro es crearlo.", author: "Peter Drucker" },
            { text: "El único límite es el que tú mismo te pones.", author: "Anónimo" },
            { text: "La vida comienza al final de tu zona de confort.", author: "Neale Donald Walsch" },
            { text: "No esperes a que pase la tormenta, aprende a bailar bajo la lluvia.", author: "Anónimo" },
            { text: "No dejes que el miedo a perder sea mayor que la emoción de ganar.", author: "Robert Kiyosaki" },
            { text: "El fracaso es la oportunidad de comenzar de nuevo con más inteligencia.", author: "Henry Ford" },
            { text: "La perseverancia no es una carrera larga; son muchas carreras cortas una tras otra.", author: "Walter Elliot" },
            { text: "El éxito es la capacidad de ir de fracaso en fracaso sin perder el entusiasmo.", author: "Winston Churchill" },
            { text: "No te rindas. El principio siempre es lo más difícil.", author: "Anónimo" },
            { text: "El único modo de hacer un gran trabajo es amar lo que haces.", author: "Steve Jobs" },
            { text: "La vida es 10% lo que te sucede y 90% cómo reaccionas ante ello.", author: "Charles R. Swindoll" },
            { text: "No importa cuán lento vayas, siempre y cuando no te detengas.", author: "Confucio" },
            { text: "El futuro pertenece a quienes creen en la belleza de sus sueños.", author: "Eleanor Roosevelt" },
            { text: "No esperes. El momento nunca será el ideal.", author: "Napoleón Hill" },
            { text: "Haz lo que puedas, con lo que tengas, donde estés.", author: "Theodore Roosevelt" },
            { text: "Cree que puedes y ya estás a mitad de camino.", author: "Theodore Roosevelt" },
            { text: "La educación es el arma más poderosa que puedes usar para cambiar el mundo.", author: "Nelson Mandela" },
            { text: "La mente es todo. Lo que piensas, te conviertes.", author: "Buda" },
            { text: "No hay viento favorable para el que no sabe a qué puerto se dirige.", author: "Séneca" },
            { text: "La vida no se trata de encontrarte a ti mismo, sino de crearte a ti mismo.", author: "George Bernard Shaw" },
            { text: "El mejor momento para plantar un árbol fue hace 20 años. El segundo mejor momento es ahora.", author: "Proverbio chino" },
            { text: "Tu tiempo es limitado, no lo desperdicies viviendo la vida de otro.", author: "Steve Jobs" },
            { text: "La simplicidad es la máxima sofisticación.", author: "Leonardo da Vinci" },
            { text: "Lo que no te mata te hace más fuerte.", author: "Friedrich Nietzsche" },
            { text: "La paciencia es amarga, pero su fruto es dulce.", author: "Jean-Jacques Rousseau" },
            { text: "El conocimiento es poder.", author: "Francis Bacon" },
            { text: "La imaginación es más importante que el conocimiento.", author: "Albert Einstein" },
            { text: "No puedes cruzar el mar simplemente mirando el agua.", author: "Rabindranath Tagore" },
            { text: "El que tiene un porqué para vivir puede soportar casi cualquier cómo.", author: "Friedrich Nietzsche" },
            { text: "La vida es realmente simple, pero insistimos en hacerla complicada.", author: "Confucio" },
            { text: "No juzgues cada día por la cosecha que recoges, sino por las semillas que plantas.", author: "Robert Louis Stevenson" },
            { text: "El único lugar donde el éxito viene antes que el trabajo es en el diccionario.", author: "Vidal Sassoon" },
            { text: "No importa cuántas veces fracases, solo debes acertar una vez.", author: "Mark Cuban" },
            { text: "Los obstáculos son esas cosas atemorizantes que ves cuando apartas los ojos de tu meta.", author: "Henry Ford" },
            { text: "La acción es la clave fundamental para todo éxito.", author: "Pablo Picasso" },
            { text: "No sueñes tu vida, vive tu sueño.", author: "Anónimo" },
            { text: "El secreto del éxito es la constancia del propósito.", author: "Benjamin Disraeli" },
            { text: "No encuentres la falta, encuentra el remedio.", author: "Henry Ford" },
            { text: "La motivación te pone en marcha, el hábito te mantiene en movimiento.", author: "Jim Ryun" },
            { text: "No dejes que lo que no puedes hacer interfiera con lo que puedes hacer.", author: "John Wooden" },
            { text: "Trabaja duro en silencio, deja que tu éxito haga el ruido.", author: "Frank Ocean" },
            { text: "Los ganadores nunca se rinden y los que se rinden nunca ganan.", author: "Vince Lombardi" },
            { text: "El éxito no es accidente. Es trabajo duro, perseverancia, aprendizaje, estudio, sacrificio y amor por lo que haces.", author: "Pelé" },
            { text: "El dolor que sientes hoy es la fuerza que sentirás mañana.", author: "Anónimo" },
            { text: "Nunca es demasiado tarde para ser lo que podrías haber sido.", author: "George Eliot" },
            { text: "La disciplina es el puente entre metas y logros.", author: "Jim Rohn" },
            { text: "No busques el momento perfecto, solo busca el momento y hazlo perfecto.", author: "Anónimo" },
            { text: "No te preocupes por los fracasos, preocúpate por las oportunidades que pierdes cuando ni siquiera lo intentas.", author: "Jack Canfield" }
        ];

        let currentQuote = 0;

        function newQuote() {
            currentQuote = Math.floor(Math.random() * quotes.length);
            document.getElementById('quoteText').textContent = '"' + quotes[currentQuote].text + '"';
            document.getElementById('quoteAuthor').textContent = '— ' + quotes[currentQuote].author;
            document.getElementById('counter').textContent = 'Frase ' + (currentQuote + 1) + ' de ' + quotes.length;
        }
    </script>
</body>
</html>
