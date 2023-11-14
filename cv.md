# Yauheni Radzivonau
***
## Senior PHP Developer

**Contact Information:**
- **Phone Number:** +5555555
- **E-mail:** iamsenior@gmail.com
- **Linkedin:** https://www.linkedin.com/in/iamsenior
***
### About:
* Senior PHP Developer with over 8 years of experience in developing web applications and websites. 
* Skilled in Object Oriented Programming, MySQL, PostgreSQL, PHP, Docker. 
* Have a deep knowledge of popular open source frameworks such as Symfony. 
* Self-motivated professional with a passion for delivering high quality code.
***
### Skills and proficiency:

- Symfony 4.4 - 6.2
- API Platform
- ES6
- Javascript
- Scrum workflow processes
- Design patterns and principles
- PHP 5.6 - 8.2
- MySQL
- PostgreSQL
- Software best practices
- Docker
- WHMCS
- Doctrine
- Twig
- Ubuntu
- Drupal
- Bootstrap
- Ubersmith
- GIT
- PHPunit
- Integration testing
- Elasticsearch
- Redis
- RabbitMQ
- Kafka
- MongoDB
***
### Code Example:
```
<?php

declare(strict_types=1);

namespace App\Command;

use App\Exception\HttpResponseException;
use App\Exception\MusementCityProcessingException;
use App\WeatherForecast\WeatherForecastDetector;
use Psr\Log\LoggerInterface;
use Symfony\Component\Console\Command\Command;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;
use Symfony\Contracts\HttpClient\Exception\ExceptionInterface;

final class WeatherForecast extends Command
{
    private const ARGUMENT_DAYS = 'days';

    private WeatherForecastDetector $weatherForecastDetector;
    private LoggerInterface $logger;

    /**
     * @param WeatherForecastDetector $weatherForecastDetector
     * @param LoggerInterface $logger
     * @param string|null $name
     */
    public function __construct(
        WeatherForecastDetector $weatherForecastDetector,
        LoggerInterface $logger,
        string $name = null
    ) {
        parent::__construct($name);

        $this->weatherForecastDetector = $weatherForecastDetector;
        $this->logger = $logger;
    }

    /**
     * {@inheritdoc}
     */
    protected function configure(): void
    {
        $this->addOption(
            self::ARGUMENT_DAYS,
            null,
            InputArgument::OPTIONAL,
            'Number of days to generate forecast.',
            '2'
        );
    }

    /**
     * {@inheritdoc}
     */
    protected function execute(InputInterface $input, OutputInterface $output): int
    {
        try {
            $days = $input->getOption(self::ARGUMENT_DAYS);

            if (!\is_string($days) || !is_numeric($days)) {
                $output->writeln('<error>Number of days should be numeric value.</error>');

                return self::FAILURE;
            }

            $this->weatherForecastDetector->detect((int) $days);

            return self::SUCCESS;
        } catch (HttpResponseException | ExceptionInterface | MusementCityProcessingException $exception) {
            $output->writeln(sprintf('<error>%s</error>', $exception->getMessage()));
        } catch (\Throwable $exception) {
            $output->writeln('<error>Unexpected error occurred, please see logs for details.</error>');
            $this->logger->error($exception->getMessage());
        }

        return self::FAILURE;
    }
}
```
***
## Work Experience:
- Junior PHP-Developer in **Company for Juniors** (2012-2014)
- Middle PHP-Developer in **Company for Middles** (2014-2017)
- Senior PHP-Developer in **Company for Seniors** (2017-current)
***
## Courses:
- RS-School Nodejs (completed)
- RS-School "Javascript-Frontend" (in progress)

***
## Languages:
- English - Advanced
- Czech - Basic
- Polish - Basic
