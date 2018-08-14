# Ansible role for sidekiq

This sets up sidekiq systemctl service on ubuntu xenial.

## Example playbook

Example usage:

    - role: thermistor.sidekiq
      sidekiq_user: beep
      sidekiq_dir: /srv/www/beep.eco/beep
      tags:
        - sidekiq

You can also specify the queues. This will create command-line args that
override a `config/sidekiq.yml` if present in the app:

    - role: thermistor.sidekiq
      sidekiq_queues:
        - mailers
        - default
      sidekiq_user: beep
      sidekiq_dir: /srv/www/beep.eco/beep
      tags:
        - sidekiq

You can specify a sidekiq role more than once in a playbook. You might want to
do this to if you want a [reserved queue](https://github.com/mperham/sidekiq/wiki/Advanced-Options#reserved-queues) for high priority jobs. For this to work you must provide a unique `sidekiq_instance`
name for each runner:

    - role: thermistor.sidekiq
      sidekiq_instance: mailers
      sidekiq_queues:
        - mailers
      sidekiq_user: beep
      sidekiq_dir: /srv/www/beep.eco/beep
      tags:
        - sidekiq
    - role: thermistor.sidekiq
      sidekiq_instance: default
      sidekiq_queues:
        - default
      sidekiq_user: beep
      sidekiq_dir: /srv/www/beep.eco/beep
      tags:
        - sidekiq

## License

MIT
