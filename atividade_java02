import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
import java.time.LocalDateTime;

// Enumeração para os diferentes níveis de log
enum Level {
    DEBUG, WARNING, ERROR
}

// Classe Logger com visibilidade de pacote
class Logger {
    // Método log com visibilidade de pacote
    static void log(Level level, String message) {
        // Obter a hora corrente
        LocalDateTime timestamp = LocalDateTime.now();
        String logEntry = "[" + timestamp + "] [" + level + "]: " + message;

        // Imprimir mensagem no console com cores diferentes com base no nível do log
        switch (level) {
            case DEBUG:
                System.out.println("\033[92m" + logEntry + "\033[0m");
                break;
            case WARNING:
                System.out.println("\033[93m" + logEntry + "\033[0m");
                break;
            case ERROR:
                System.out.println("\033[91m" + logEntry + "\033[0m");
                break;
        }
    }
}

// Classe LoggerFactory com visibilidade de pacote
class LoggerFactory {
    // Método onConsole com visibilidade de pacote
    static Logger onConsole() {
        return new Logger();
    }

    // Método onFile com visibilidade de pacote
    static Logger onFile(String fileName) throws IOException {
        return new FileLogger(fileName);
    }
}

// Classe LoggerConsole com visibilidade de pacote
class LoggerConsole {
    // Método log com visibilidade de pacote
    static void log(Level level, String message) {
        Logger.log(level, message);
    }
}

// Classe LoggerFile com visibilidade de pacote
class LoggerFile {
    // Método log com visibilidade de pacote
    static void log(Level level, String message) {
        try (PrintWriter writer = new PrintWriter(new FileWriter("log.txt", true))) {
            // Obter a hora corrente
            LocalDateTime timestamp = LocalDateTime.now();
            String logEntry = "[" + timestamp + "] [" + level + "]: " + message;
            // Escrever no arquivo
            writer.println(logEntry);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

public class Main {
    public static void main(String[] args) {
        // Exemplo de uso
        LoggerConsole.log(Level.DEBUG, "This is a debug message");
        LoggerConsole.log(Level.WARNING, "This is a warning message");
        LoggerConsole.log(Level.ERROR, "This is an error message");

        try {
            LoggerFile.log(Level.DEBUG, "This is a debug message");
            LoggerFile.log(Level.WARNING, "This is a warning message");
            LoggerFile.log(Level.ERROR, "This is an error message");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
