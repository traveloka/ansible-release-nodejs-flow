# release/enterprise-nodejs

Release a NodeJS service with Enterprise team
preference of the steps:

   - Stop the service first, because with
     rolling / immutable deployment, it is okay.

   - Use the same s3-deploy-object role used by
     Java stacks.

   - Start service with "npm start". You can use
     environment in playbook that using this role,
     but the role itself should be kept simple.

## Requirements

This is assuming NPM is exist, without explicit dependencies.

## Role Variables

   - name: service_name
     desc: Name of the service.

   - name: service_version
     desc: Service of the version.

## Dependencies

   - npm-stop
   - s3-deploy-object
   - unarchive-cleanup
   - npm-start

## Example Playbook

   - hosts: servers
     roles:
       - role: release/enterprise-nodejs
         service_name: enterprise-frontend