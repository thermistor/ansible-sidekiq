# Ansible role for sidekiq

This sets up sidekiq systemctl service on ubuntu xenial.

## Example playbook

Example usage:

    - role: thermistor.sidekiq
      sidekiq_user: beep
      sidekiq_dir: /srv/www/beep.eco/beep
      tags:
        - sidekiq

you can also specify the queues if not using a `sidekiq.conf`:

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

