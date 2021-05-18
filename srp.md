# Single responsibility principle

Single responsibility principle as indicates shall handle only one responsibility it is assigned. This will hepl is code re usability, to refactor the code in terms of design change.

Below example provides an example of logger class.
1. Here SystemLogger and FileLogger are having responsibility of logging with their respective mechanism.
2. Logger class knows only to redirect the log message based on the instance it is provded. 


public interface ILogger
    {
        void Log(string message);
    }

    public class Logger
    {
        private ILogger _logger;
        public Logger(ILogger logger)
        {
            _logger = logger;
        }

        public void Log(string message)
        {
            _logger.Log(message);
        }
    }

    public class SystemLogger : ILogger
    {
        public void Log(string message)
        {
            // writes in system specified log
        }
    }

    public class FileLogger : ILogger
    {
        public void Log(string message)
        {
            // writes in file
        }
    }
