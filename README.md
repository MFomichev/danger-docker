# danger-docker
Docker wrapper for danger

# Launch on GitLab CI
docker run --rm -i \
      -v $(pwd):/apps \
      --env-file <(env | \
      grep -vE "(PATH|HOSTNAME|RUBY_DOWNLOAD_SHA256|RUBY_VERSION|PWD|BUNDLE_APP_CONFIG|RUBY_MAJOR|HOME\
      |LANG|BUNDLE_SILENCE_ROOT_WARNING|GET_HOME|SHLVL|TERM)") \
      -e CI_PROJECT_PATH="wms/warehouse-app" \
      mfomichev/danger:8.2.3 \
      bash -c "danger --fail-if-no-pr=true"
