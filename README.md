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

## License

MIT

