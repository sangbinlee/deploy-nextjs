# deploy-nextjs






# git pull
    
    
    root@ns1:/home/sangbinlee9/front-end/mini-do# git pull
    remote: Enumerating objects: 6, done.
    remote: Counting objects: 100% (6/6), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 4 (delta 2), reused 4 (delta 2), pack-reused 0
    Unpacking objects: 100% (4/4), 1.36 KiB | 1.36 MiB/s, done.
    From https://github.com/sangbinlee/mini-do
       75eb893..07bc6f1  main       -> origin/main
    Updating 75eb893..07bc6f1
    Fast-forward
     docker-compose.prod.yml |  2 +-
     prod.Dockerfile         | 73 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
     2 files changed, 74 insertions(+), 1 deletion(-)
     create mode 100644 prod.Dockerfile
    



# docker compose -f docker-compose.prod.yml build
     
    root@ns1:/home/sangbinlee9/front-end/mini-do# docker compose -f docker-compose.prod.yml build
    [+] Building 28.5s (15/18)                                                                                                                                                                                                                                                                               docker:default
     => [mini-do internal] load build definition from prod.Dockerfile                                                                                                                                                                                                                                                  0.0s
     => => transferring dockerfile: 2.53kB                                                                                                                                                                                                                                                                             0.0s
     => [mini-do internal] load .dockerignore                                                                                                                                                                                                                                                                          0.0s
     => => transferring context: 2B                                                                                                                                                                                                                                                                                    0.0s
     => [mini-do internal] load metadata for docker.io/library/node:18-alpine                                                                                                                                                                                                                                          1.6s
     => [mini-do internal] load build context                                                                                                                                                                                                                                                                          0.3s
     => => transferring context: 2.38kB                                                                                                                                                                                                                                                                                0.2s
     => [mini-do base 1/1] FROM docker.io/library/node:18-alpine@sha256:3428c2de886bf4378657da6fe86e105573a609c94df1f7d6a70e57d2b51de21f                                                                                                                                                                               0.0s
     => CACHED [mini-do builder 1/8] WORKDIR /app                                                                                                                                                                                                                                                                      0.0s
     => [mini-do runner 2/6] RUN addgroup --system --gid 1001 nodejs                                                                                                                                                                                                                                                   0.4s
     => CACHED [mini-do builder 2/8] COPY package.json yarn.lock* package-lock.json* pnpm-lock.yaml* ./                                                                                                                                                                                                                0.0s
     => CACHED [mini-do builder 3/8] RUN   if [ -f yarn.lock ]; then yarn --frozen-lockfile;   elif [ -f package-lock.json ]; then npm ci;   elif [ -f pnpm-lock.yaml ]; then yarn global add pnpm && pnpm i;   else echo "Warning: Lockfile not found. It is recommended to commit lockfiles to version control." &&  0.0s
     => CACHED [mini-do builder 4/8] COPY src ./src                                                                                                                                                                                                                                                                    0.0s
     => CACHED [mini-do builder 5/8] COPY public ./public                                                                                                                                                                                                                                                              0.0s
     => CACHED [mini-do builder 6/8] COPY next.config.js .                                                                                                                                                                                                                                                             0.0s
     => CACHED [mini-do builder 7/8] COPY tsconfig.json .                                                                                                                                                                                                                                                              0.0s
     => ERROR [mini-do builder 8/8] RUN   if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi                                                                                                           26.5s
     => [mini-do runner 3/6] RUN adduser --system --uid 1001 nextjs                                                                                                                                                                                                                                                    0.5s
    ------
     > [mini-do builder 8/8] RUN   if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi:
    0.637 yarn run v1.22.19
    0.708 $ next build
    1.571 Attention: Next.js now collects completely anonymous telemetry regarding usage.
    1.571 This information is used to shape Next.js' roadmap and prioritize features.
    1.572 You can learn more, including how to opt-out if you'd not like to participate in this anonymous program, by visiting the following URL:
    1.572 https://nextjs.org/telemetry
    1.572
    1.715    ▲ Next.js 14.0.3
    1.715
    1.716    Creating an optimized production build ...
    19.11  ✓ Compiled successfully
    19.11    Linting and checking validity of types ...
    25.33    Collecting page data ...
    25.98 Error: @prisma/client did not initialize yet. Please run "prisma generate" and try to import it again.
    25.98 In case this error is unexpected for you, please report it in https://github.com/prisma/prisma/issues
    25.98     at new PrismaClient (/app/node_modules/.prisma/client/index.js:43:11)
    25.98     at 92823 (/app/.next/server/app/api/todos/[id]/route.js:1:2652)
    25.98     at t (/app/.next/server/webpack-runtime.js:1:128)
    25.98     at 52614 (/app/.next/server/app/api/todos/[id]/route.js:1:721)
    25.98     at t (/app/.next/server/webpack-runtime.js:1:128)
    25.98     at r (/app/.next/server/app/api/todos/[id]/route.js:1:2988)
    25.98     at /app/.next/server/app/api/todos/[id]/route.js:1:3023
    25.98     at t.X (/app/.next/server/webpack-runtime.js:1:1196)
    25.98     at /app/.next/server/app/api/todos/[id]/route.js:1:3001
    25.98     at Object.<anonymous> (/app/.next/server/app/api/todos/[id]/route.js:1:3051)
    25.99
    25.99 > Build error occurred
    25.99 Error: Failed to collect page data for /api/todos/[id]
    25.99     at /app/node_modules/next/dist/build/utils.js:1217:15
    25.99     at process.processTicksAndRejections (node:internal/process/task_queues:95:5) {
    25.99   type: 'Error'
    25.99 }
    26.08 error Command failed with exit code 1.
    26.08 info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
    ------
    failed to solve: process "/bin/sh -c if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi" did not complete successfully: exit code: 1
    root@ns1:/home/sangbinlee9/front-end/mini-do# docker compose -f docker-compose.prod.yml up -d
    [+] Building 27.3s (15/18)                                                                                                                                                                                                                                                                               docker:default
     => [mini-do internal] load build definition from prod.Dockerfile                                                                                                                                                                                                                                                  0.0s
     => => transferring dockerfile: 2.53kB                                                                                                                                                                                                                                                                             0.0s
     => [mini-do internal] load .dockerignore                                                                                                                                                                                                                                                                          0.0s
     => => transferring context: 2B                                                                                                                                                                                                                                                                                    0.0s
     => [mini-do internal] load metadata for docker.io/library/node:18-alpine                                                                                                                                                                                                                                          0.7s
     => [mini-do internal] load build context                                                                                                                                                                                                                                                                          0.2s
     => => transferring context: 2.38kB                                                                                                                                                                                                                                                                                0.2s
     => [mini-do base 1/1] FROM docker.io/library/node:18-alpine@sha256:3428c2de886bf4378657da6fe86e105573a609c94df1f7d6a70e57d2b51de21f                                                                                                                                                                               0.0s
     => CACHED [mini-do builder 1/8] WORKDIR /app                                                                                                                                                                                                                                                                      0.0s
     => CACHED [mini-do runner 2/6] RUN addgroup --system --gid 1001 nodejs                                                                                                                                                                                                                                            0.0s
     => CACHED [mini-do runner 3/6] RUN adduser --system --uid 1001 nextjs                                                                                                                                                                                                                                             0.0s
     => CACHED [mini-do builder 2/8] COPY package.json yarn.lock* package-lock.json* pnpm-lock.yaml* ./                                                                                                                                                                                                                0.0s
     => CACHED [mini-do builder 3/8] RUN   if [ -f yarn.lock ]; then yarn --frozen-lockfile;   elif [ -f package-lock.json ]; then npm ci;   elif [ -f pnpm-lock.yaml ]; then yarn global add pnpm && pnpm i;   else echo "Warning: Lockfile not found. It is recommended to commit lockfiles to version control." &&  0.0s
     => CACHED [mini-do builder 4/8] COPY src ./src                                                                                                                                                                                                                                                                    0.0s
     => CACHED [mini-do builder 5/8] COPY public ./public                                                                                                                                                                                                                                                              0.0s
     => CACHED [mini-do builder 6/8] COPY next.config.js .                                                                                                                                                                                                                                                             0.0s
     => CACHED [mini-do builder 7/8] COPY tsconfig.json .                                                                                                                                                                                                                                                              0.0s
     => ERROR [mini-do builder 8/8] RUN   if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi                                                                                                           26.3s
    ------
     > [mini-do builder 8/8] RUN   if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi:
    0.489 yarn run v1.22.19
    0.517 $ next build
    1.333 Attention: Next.js now collects completely anonymous telemetry regarding usage.
    1.333 This information is used to shape Next.js' roadmap and prioritize features.
    1.333 You can learn more, including how to opt-out if you'd not like to participate in this anonymous program, by visiting the following URL:
    1.333 https://nextjs.org/telemetry
    1.333
    1.478    ▲ Next.js 14.0.3
    1.478
    1.479    Creating an optimized production build ...
    18.87  ✓ Compiled successfully
    18.87    Linting and checking validity of types ...
    25.13    Collecting page data ...
    25.76 Error: @prisma/client did not initialize yet. Please run "prisma generate" and try to import it again.
    25.76 In case this error is unexpected for you, please report it in https://github.com/prisma/prisma/issues
    25.76     at new PrismaClient (/app/node_modules/.prisma/client/index.js:43:11)
    25.76     at 92823 (/app/.next/server/app/api/todos/route.js:1:2033)
    25.76     at t (/app/.next/server/webpack-runtime.js:1:128)
    25.76     at 3357 (/app/.next/server/app/api/todos/route.js:1:716)
    25.76     at t (/app/.next/server/webpack-runtime.js:1:128)
    25.76     at r (/app/.next/server/app/api/todos/route.js:1:2366)
    25.76     at /app/.next/server/app/api/todos/route.js:1:2401
    25.76     at t.X (/app/.next/server/webpack-runtime.js:1:1196)
    25.76     at /app/.next/server/app/api/todos/route.js:1:2379
    25.76     at Object.<anonymous> (/app/.next/server/app/api/todos/route.js:1:2428)
    25.76
    25.76 > Build error occurred
    25.77 Error: Failed to collect page data for /api/todos
    25.77     at /app/node_modules/next/dist/build/utils.js:1217:15
    25.77     at process.processTicksAndRejections (node:internal/process/task_queues:95:5) {
    25.77   type: 'Error'
    25.77 }
    25.86 error Command failed with exit code 1.
    25.86 info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
    ------
    failed to solve: process "/bin/sh -c if [ -f yarn.lock ]; then yarn build;   elif [ -f package-lock.json ]; then npm run build;   elif [ -f pnpm-lock.yaml ]; then pnpm build;   else yarn build;   fi" did not complete successfully: exit code: 1









# yarn build
    
    root@ns1:/home/sangbinlee9/front-end/mini-do# yarn build
    yarn run v1.22.21
    $ next build
       ▲ Next.js 14.0.3
       - Environments: .env
    
     ✓ Creating an optimized production build
     ✓ Compiled successfully
     ✓ Linting and checking validity of types
       Collecting page data  .xxxxxxxxxxxxxxxx environmentVariables= F {
      spa: [Function: bound safeParseAsync] AsyncFunction,
      _def: {
        shape: [Function: shape],
        unknownKeys: 'strip',
        catchall: $ {
          spa: [Function: bound safeParseAsync] AsyncFunction,
          _def: [Object],
          parse: [Function: bound parse],
          safeParse: [Function: bound safeParse],
          parseAsync: [Function: bound parseAsync] AsyncFunction,
          safeParseAsync: [Function: bound safeParseAsync] AsyncFunction,
          refine: [Function: bound refine],
          refinement: [Function: bound refinement],
          superRefine: [Function: bound superRefine],
          optional: [Function: bound optional],
          nullable: [Function: bound nullable],
          nullish: [Function: bound nullish],
          array: [Function: bound array],
          promise: [Function: bound promise],
          or: [Function: bound or],
          and: [Function: bound and],



              
      describe: [Function: bound describe],
      pipe: [Function: bound pipe],
      readonly: [Function: bound readonly],
      isNullable: [Function: bound isNullable],
      isOptional: [Function: bound isOptional],
      _cached: null,
      nonstrict: [Function: passthrough],
      augment: [Function: extend]
    }
    999999999999999= 0
     ✓ Collecting page data
     ✓ Generating static pages (5/5)
     ✓ Collecting build traces
     ✓ Finalizing page optimization
    
    Route (app)                              Size     First Load JS
    ┌ ○ /                                    94.2 kB         204 kB
    ├ ○ /_not-found                          876 B          84.8 kB
    ├ λ /api/auth/[...nextauth]              0 B                0 B
    ├ λ /api/todos                           0 B                0 B
    └ λ /api/todos/[id]                      0 B                0 B
    + First Load JS shared by all            84 kB
      ├ chunks/472-346641e24f02d8dd.js       28.7 kB
      ├ chunks/fd9d1056-e4fd05f3595a570a.js  53.3 kB
      ├ chunks/main-app-d4995ef74a41d67c.js  219 B
      └ chunks/webpack-3bad45a73e77d20d.js   1.74 kB
    
    
    ƒ Middleware                             61.7 kB
    
    ○  (Static)   prerendered as static content
    λ  (Dynamic)  server-rendered on demand using Node.js
    
    Done in 24.22s.



# yarn start

    
    root@ns1:/home/sangbinlee9/front-end/mini-do# yarn start
    yarn run v1.22.21
    $ next start
       ▲ Next.js 14.0.3
       - Local:        http://localhost:3000
    
     ✓ Ready in 408ms



![image](https://github.com/sangbinlee/deploy-nextjs/assets/4024414/1c2ed8ae-5fe6-4860-b766-15d9ec41abcb)








#  참조 문서





https://github.com/vercel/next.js/blob/canary/examples/with-docker-compose/README.md





![image](https://github.com/sangbinlee/deploy-nextjs/assets/4024414/a79b8fe8-e37f-46de-8303-c4dd5955a05f)






# I can run the process at the background using:

(npm run start&)

    
    root@ns1:/home/sangbinlee9/front-end/mini-do# (yarn start&)
    yarn run v1.22.21
    $ next start
       ▲ Next.js 14.0.3
       - Local:        http://localhost:3000
    
     ✓ Ready in 401ms
    xxxxxxxxxxxxxxxx environmentVariables= F {
      spa: [Function: bound safeParseAsync] AsyncFunction,
      _def: {
        shape: [Function: shape],



        ![image](https://github.com/sangbinlee/deploy-nextjs/assets/4024414/c4908646-e58d-4505-87d5-d5d33320831e)

